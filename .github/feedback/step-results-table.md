{%- set all_passed = (results_table | selectattr("passed") | length) == (results_table | length) %}

{%- if all_passed %}

## ステップ {{ step_number }}　完了 ✅

{%- else %}

## ステップ {{ step_number }}　要確認 ❌

確認できなかった項目があります。以下の結果を見て、もう一度試してください。

{%- endif %}

| 結果 | 確認項目 |
| --- | --- |
{%- for row in results_table %}
| {% if row.passed -%}✅ 完了{%- else -%}❌ 要確認{%- endif %} | {{ row.description }} |
{%- endfor %}

{%- if tips and tips.length %}

### ヒント

{%- for tip in tips %}
- {{ tip }}
{%- endfor %}

{%- endif %}
