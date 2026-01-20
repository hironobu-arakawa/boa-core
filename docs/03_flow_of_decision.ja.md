# Flow of Decision

このドキュメントは、  
BOA Core における **判断の進行順序** を示します。

ここで示すのはアルゴリズムではありません。  
**「判断が進んでよい条件」と「止まる条件」** だけを明確にします。

---

## 全体フロー（概念）

判断は、以下の順序でのみ進みます。

1. BOA（境界の確認）
2. IDG（判断可能性の確認）
3. RP（判断の扱いを選択）
4. RCA（責任の閉鎖）

この順序は変更できません。

---

## 擬似コード表現（概念）

```pseudo
function decision_flow(input, context):

    // 1. Boundary check
    if not BOA.allows(input, context):
        return STOP("Outside allowed boundary")

    // 2. Determinability check
    determinability = IDG.evaluate(input, context)

    if determinability == INDETERMINABLE:
        return RETURN("Cannot decide under current conditions")

    // 3. Resolution
    resolution = RP.resolve(input, context)

    if resolution == RESOLVE:
        outcome = apply_decision(input)

    else if resolution == REJECT:
        outcome = discard_decision(input)

    else if resolution == RETURN:
        return RETURN("Decision returned by protocol")

    // 4. Responsibility closure
    RCA.close(outcome, resolution, context)

    return outcome
```

---

## 各ステップの意味（重要）

### 1. BOA — Boundary Check

```pseudo
if not BOA.allows(input, context):
    STOP
```

BOA は最初に必ず評価されます。

ここでの `STOP` は エラーではありません。  
「判断を開始しない」という正常な終了です。

BOA は、  
判断の正当性ではなく、判断の許可領域を扱います。

### 2. IDG — Determinability Check

```pseudo
if determinability == INDETERMINABLE:
    RETURN
```

判断不能は失敗ではありません。  
判断不能は「戻す」理由になります。

ここでは RP は起動しません。

IDG が通らない状態で判断を進めることは、  
設計違反です。

### 3. RP — Resolution

```pseudo
resolution = RP.resolve(...)
```

RP は、判断結果を計算しません。  
RP が決めるのは 「この判断をどう扱うか」 です。

RP が返せる値は、必ず以下のいずれかです。

**RESOLVE | REJECT | RETURN**

沈黙・暗黙・デフォルトは存在しません。

### 4. RCA — Responsibility Closure

```pseudo
RCA.close(outcome, resolution, context)
```

RCA は、  
判断の成否や品質を評価しません。

RCA が行うのは、

- この判断は誰の責任か
- どの判断が、どの条件で行われたか
- どこまでが自動で、どこからが人か

を 残すことです。

## このフローが守っている不変条件

この構造には、以下の不変条件があります。

- BOA を通らずに判断は始まらない
- IDG を通らずに RP は起動しない
- RP は必ず明示的な結果を返す
- RCA を通らない判断は「存在しない」

## 実装への注意（重要）

この擬似コードは、  
実装例ではありません。

- 同期 / 非同期は規定しません
- 例外処理方法は規定しません
- 言語・フレームワークを想定しません

ここで示しているのは、

> 判断が壊れないために  
> 必ず守られるべき流れ

のみです。

## 次に読むもの

判断が止まる理由と、その正当性  
→ [04_failure_and_stop.md](04_failure_and_stop.md)