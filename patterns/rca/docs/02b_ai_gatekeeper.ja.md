# AI Gatekeeper (Decision Closure Structure)

AI Gatekeeper は、AI が自身の出力によって判断を「閉じてよいか」を判定する実装構造です。
概念としての **Decision Closure** を、用途未定義世界において安全に実行するためのプロトコルです。

判断の結果は常に次の二択です。

- **AI-Closed**：AI の出力で判断が完結してよい
- **Human-Closed**：AI は判断を閉じず、人に返す

デフォルトは Human-Closed です。

---

## 判断閉路の5ステップ

AI Gatekeeper は、次の5ステップで判定を行います。
いずれかが破綻した時点で Human-Closed に遷移します。

1. **Responsibility Scope** (責任主体の単一性): 責任主体は1人か
2. **No Psychological Revocation** (心理的取消への非依存): 心理的取消に依存していないか
3. **Physical Revocability** (物理的可逆性): 物理的に直接取り消せるか
4. **No Action Chaining** (行動連鎖の欠如): 行動が連鎖しないか
5. **No Social Context** (社会的文脈の欠如): 社会的文脈を帯びていないか

心理的取消（空気を読めば止められる等）は、
設計上「存在しない」と扱います。

---

## 精度を扱わない理由

本構造では「精度」を直接扱いません。

用途未定義世界では、
どこまで正確である必要があるかが分からないためです。

代わりに、
- 間違っても直接取り消せるか
という **可逆性** に置き換えて判定します。
