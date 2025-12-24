# PIDSMaker框架研究笔记

## 配置
1. 数据库创建方式(以optc_501.dump为例)：
    ```
    # 进入数据库容器并创建新库：
    docker compose -p postgres exec postgres createdb -U postgres optc_501
    # 重新导入数据到这个新库里（注意 -d 参数变成了 optc_501）：
    docker compose -p postgres exec postgres pg_restore -U postgres -d optc_501 /data/optc_501.dump
    ```

## 常见报错
1. 运行`pidsmaker/main.py`，出现`Killed`:
    * 当前方法会全量加载数据集https://github.com/ubc-provenance/PIDSMaker/issues/9
    * 训练阶段内存开销可能大于32GB
