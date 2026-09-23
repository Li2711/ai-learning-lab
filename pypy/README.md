# pypy-scripts

Python 学习与练习脚本仓库。

## 目录结构

```
pypy-scripts/
├── script/
│   └── 01.ipynb      # Jupyter 练习笔记本
├── .venv/            # 本地虚拟环境（已在 .gitignore 中排除，不入库）
└── .gitignore
```

## 环境说明

本仓库使用本地虚拟环境 `.venv`，**不纳入版本控制**。克隆本仓库后需要自行创建：

```bash
python -m venv .venv
.venv/Scripts/activate      # Windows
pip install jupyter         # 按需安装依赖
```

## 说明

- `.venv/` 体积约 109MB、含 9500+ 文件，提交它会导致 Git 仓库臃肿并可能触发 GitHub 的推送限制，因此在 `.gitignore` 中排除。
- 如需记录依赖，建议导出 `requirements.txt`：`pip freeze > requirements.txt`。
