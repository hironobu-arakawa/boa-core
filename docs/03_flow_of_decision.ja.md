# Flow of Decision

このドキュメントは、
BOA Core における **判断の進行順序** を示します。

ここで示すのはアルゴリズムではありません。
**「判断が進んでよい条件」と「止まる条件」** だけを明確にします。

---

## 全体フロー（概念）

判断は、以下の順序でのみ進みます。

1. **BOA** （境界の確認 - どこで？）
2. **RCA** （責任の引き受け - 誰が？）
3. **RP**  （解決の認定 - どう扱う？）

この順序は変更できません。

---

## 擬似コード表現（概念）

```pseudo
function decision_flow(input, context):

    // 1. Boundary check (BOA)
    // 境界内に収まっているか？
    if not BOA.allows(input, context):
        return STOP("Outside allowed boundary")

    // 2. Responsibility Assessment (RCA)
    // エージェントは責任を引き受けるか？
    assessment = RCA.assess(input, context)

    if assessment.state == DENIED:
         return STOP("RCA denied responsibility: " + assessment.reason)
    
    if assessment.state == UNKNOWN:
         return ESCALATE("RCA cannot decide: " + assessment.reason)

    // assessment.state == ACCEPTED の場合のみ進む

    // 3. Resolution Protocol (RP)
    // その引き受けはプロトコルに適合しているか？
    resolution = RP.verify_and_promote(assessment)

    if resolution == PROMOTED_TO_RESOLUTION:
        return COMMIT_RESOLUTION(resolution)
    
    else:
        return ROUTE(resolution.routing_instruction)
```

---

## 各ステップの意味（重要）

### 1. BOA — Boundary Check

```pseudo
if not BOA.allows(input, context):
    STOP
```

BOA は最初に必ず評価されます。
ここでの `STOP` はエラーではありません。「判断を開始しない」という正常な終了です。

### 2. RCA — Responsibility Assessment

```pseudo
assessment = RCA.assess(input, context)
```

RCAは、入力された判断案件に対して **「主体としての意思」** を示します。

-   **ACCEPTED**: 「私が責任を持ちます（署名）」
-   **DENIED**: 「私は判断しません（拒否）」
-   **UNKNOWN**: 「判断できません（不明）」

これは、機械的な判定を超えた能動的なステップです。
RCAが首を縦に振らない限り、後続のプロセスは絶対に動きません。

### 3. RP — Resolution Protocol

```pseudo
resolution = RP.verify_and_promote(assessment)
```

RPは、RCAが「引き受ける（ACCEPTED）」と言った案件に対して、**「手続きの正当性」** を検査します。

-   署名はあるか？
-   必須項目は埋まっているか？
-   権限はあるか？

すべて適正であれば、RPはこれを **Resolution（正式な解決）** に昇格させ、確定させます。
そうでなければ、人間に戻す（Return）などのルーティングを行います。

---

## このフローが守っている不変条件

この構造には、以下の不変条件があります。

-   BOA を通らずに判断は始まらない
-   **RCA が引き受けない判断は RP に到達しない**
-   RP は必ず明示的な結果（Resolution または Routing）を返す
-   誰の責任でもない判断はシステム内に存在し得ない

---

## 実装への注意（重要）

この擬似コードは実装例ではありません。
ここで示しているのは、

> **責任の所在が不明なまま、処理が進むことを防ぐための構造**

のみです。

---

## 次に読むもの

判断が止まる理由と、その正当性
→ [04_failure_and_stop.md](04_failure_and_stop.md)