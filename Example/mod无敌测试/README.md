# 觅长生 - 主角无敌Mod

## 简介

这是一个让主角从游戏开始就处于无敌状态的Mod。启用后，主角将免疫所有伤害，让你可以轻松体验游戏内容。

## 功能特性

- 自动在进入游戏时为主角添加无敌Buff
- 可自定义无敌Buff的层数（1-100层）
- 可选择是否显示无敌效果启用提示
- 随时可以在Mod设置中启用或关闭无敌模式

## 安装方法

### 安装步骤（重要）

1. 将整个 `mod无敌测试` 文件夹复制到游戏目录的正确位置：
   ```
   觅长生/本地Mod测试/plugins/plugins/Next/mod无敌测试
   ```

   **注意**：
   - 必须放在 `本地Mod测试/plugins/plugins/Next/` 目录下
   - 如果 `plugins/plugins/Next/` 文件夹不存在，请先创建这些文件夹
   - 文件夹名必须以 `mod` 开头（已满足）

2. 确认文件夹结构正确：
   ```
   觅长生/
   └── 本地Mod测试/
       └── plugins/
           └── plugins/
               └── Next/
                   └── mod无敌测试/
                       ├── Config/
                       ├── Data/
                       └── NData/
   ```

3. 启动游戏，Mod会自动加载（无需手动启用）

4. 开始新游戏或加载存档，无敌效果将自动生效

## 使用说明

### 使用无敌效果

1. 确保Mod已正确安装在 `本地Mod测试/plugins/plugins/Next/mod无敌测试` 目录
2. 启动游戏，Mod会自动加载
3. 进入游戏后，无敌效果将自动添加到主角
4. 你会看到提示："检测到无敌Mod已启用...无敌效果已添加！"

### 修改配置选项（可选）

Mod配置文件位于：`mod无敌测试/Config/modConfig.json`

你可以编辑此文件来修改以下设置：

- **EnableInvincible**：控制是否启用无敌模式（默认：true）
- **InvincibleBuffLayer**：设置无敌Buff的叠加层数，1-100（默认：10）
- **ShowNotification**：控制是否显示启用提示（默认：true）

修改后保存文件，重启游戏即可生效。

### 关闭无敌效果

如需关闭无敌效果，有两种方法：

**方法1**：编辑配置文件
- 打开 `Config/modConfig.json`
- 找到 `"EnableInvincible"` 对应的 `DefaultValue`，改为 `false`
- 保存并重启游戏

**方法2**：删除/移动Mod文件夹
- 将 `mod无敌测试` 文件夹从 `plugins/Next/` 目录移出
- 重启游戏

## 文件结构

```
mod无敌测试/
├── Config/
│   └── modConfig.json              # Mod配置文件
├── NData/
│   ├── DialogEvent/
│   │   └── invincible.json         # 无敌剧情事件
│   └── DialogTrigger/
│       └── trigger.json            # 自动触发器
├── Data/
│   ├── BuffJsonData/
│   │   └── 999.json                # 无敌Buff数据
│   └── BuffSeidJsonData/
│       └── 4.json                  # Buff效果数据（抵挡伤害）
└── README.md                        # 本说明文件
```

## 技术说明

### 实现原理

本Mod通过以下方式实现无敌效果：

1. **自定义Buff**：创建了一个ID为999的无敌Buff
2. **Buff效果**：使用BuffSeid ID 4（抵挡伤害），设置极大的抵挡值（999999999点）
3. **自动触发**：使用"进入游戏"触发器，在玩家进入游戏时自动执行
4. **条件判断**：通过设置中的"启用无敌模式"开关控制是否启用
5. **先天Buff**：使用先天Buff系统，确保Buff持续存在

### Buff数据说明

- **Buff ID**: 999
- **Buff名称**: 无敌
- **BuffSeid类型**: 4（抵挡伤害）
- **持续时间**: 999999回合（接近永久）
- **抵挡伤害值**: 999999999（可抵挡极高伤害）

### BuffSeid说明

游戏使用BuffSeid系统来定义Buff的具体效果：
- **ID 4 - 抵挡伤害**：每层Buff可抵挡固定数值的伤害
- **value1**: 抵挡的伤害数值（999999999点，实际上可以抵挡所有伤害）
- 配置文件：`Data/BuffSeidJsonData/4.json`

### 自定义修改

如果你想调整无敌效果，可以修改以下文件：

1. **调整Buff持续时间**：编辑 `Data/BuffJsonData/999.json` 的 `totaltime` 字段
2. **调整抵挡伤害数值**：编辑 `Data/BuffSeidJsonData/4.json` 的 `value1` 字段
3. **修改触发条件**：编辑 `NData/DialogTrigger/trigger.json` 的 `condition` 字段
4. **自定义提示信息**：编辑 `NData/DialogEvent/invincible.json` 的 `dialog` 数组

## 注意事项

1. 本Mod会使游戏失去挑战性，建议仅在体验剧情或测试时使用
2. 无敌效果只影响主角，不影响NPC和宠物
3. 某些特殊剧情可能会强制设定角色状态，可能导致无敌效果暂时失效
4. 建议在新游戏时启用，避免对现有存档造成影响
5. 如遇到问题，可以尝试关闭Mod后重新启动游戏

## 兼容性

- 与大部分其他Mod兼容
- 不会修改游戏原有数据，只是添加新的Buff
- 卸载后不会对游戏造成负面影响

## 版本历史

- **v1.0.0** (2025-11-09)
  - 首次发布
  - 实现基础无敌功能
  - 添加可配置选项

## 作者

Claude

## 许可证

本Mod免费开源，可自由修改和分发。

## 反馈

如有问题或建议，欢迎反馈！
