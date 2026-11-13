{{#passed}}
## ステップ {{ step_number }}　完了 ✅
{{/passed}}
{{^passed}}
## ステップ {{ step_number }}　要確認 ❌

以下の結果を確認して、もう一度試してください。
{{/passed}}

| 結果 | 確認項目 |
| --- | --- |
{{#results_table}}
| {{#passed}}✅ 完了{{/passed}}{{^passed}}❌ 要確認{{/passed}} | {{ description }} |
{{/results_table}}

{{#tips.length}}
### ヒント

{{#tips}}
- {{.}}
{{/tips}}
{{/tips.length}}
