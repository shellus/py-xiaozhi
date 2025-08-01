# 12306查询工具 (Railway Tools)

火车票查询工具是一个基于12306系统的 MCP 工具集，提供了火车票查询、车站信息查询、中转方案查询等功能。工具提供了两层接口：**智能工具**（用户友好的自然语言接口）和**原子工具**（技术开发接口）。

## 智能工具（推荐使用）

智能工具能够理解自然语言输入，自动处理复杂的查询逻辑，是日常使用的首选方式。

### 常见使用场景

**智能火车票查询:**
- "查询明天从北京到上海的火车票"
- "我想看看后天广州到深圳的高铁"
- "帮我查一下这周六从杭州到南京的车票"
- "查询2025年1月15日北京南到天津的动车"
- "上午出发到上海的高铁有哪些"

**智能车站查询:**
- "北京有哪些火车站"
- "上海的主要火车站是哪个"  
- "查询北京南站的车站编码"
- "虹桥站的详细信息"

**智能中转查询:**
- "从北京到广州没有直达车怎么办"
- "查询从哈尔滨到昆明的中转方案"
- "我需要在郑州中转，帮我查票"

**智能出行建议:**
- "从北京到上海怎么去最好"
- "给我推荐一下从广州到深圳的出行方案"
- "我想要最快的方案去杭州"
- "经济实惠的火车票推荐"

### 使用提示

1. **使用常见城市名**: 如"北京"、"上海"、"广州"等，系统会自动匹配主要车站
2. **提供具体日期**: 支持"明天"、"后天"、"这周六"等相对时间
3. **指定车型偏好**: 可以说明偏好高铁、动车或普通列车
4. **考虑出行时间**: 可以指定出发时间段，如"上午"、"下午"等
5. **表达偏好**: 可以说明"最快"、"最便宜"、"舒适"等偏好

AI 助手会根据您的需求自动调用智能工具，为您提供准确的票务信息和出行建议。

## 智能工具详细介绍

### 1. smart_ticket_query - 智能火车票查询
自动处理自然语言火车票查询，支持相对日期、车型偏好、时间段筛选等。

**特点:**
- 自动转换城市名为车站编码
- 支持相对日期（明天、后天、这周六等）
- 智能识别车型偏好（高铁、动车、直达等）
- 按时间段筛选（上午、下午、晚上）
- 格式化输出，易于阅读

**使用示例:**
- "查询明天从北京到上海的火车票"
- "我想看看后天广州到深圳的高铁"
- "上午出发到南京的动车有哪些"

### 2. smart_transfer_query - 智能中转查询
当没有直达车时，自动查找最优中转方案，提供详细的换乘信息。

**特点:**
- 自动计算最优中转路线
- 显示换乘等待时间
- 支持指定中转城市
- 分析同站换乘和跨站换乘
- 提供完整行程信息

**使用示例:**
- "从北京到广州没有直达车怎么办"
- "查询从哈尔滨到昆明的中转方案"
- "我需要在郑州中转，帮我查票"

### 3. smart_station_query - 智能车站查询
处理各种车站相关查询，自动识别查询意图并提供相应信息。

**特点:**
- 自动识别查询类型（车站列表、主要车站、编码等）
- 支持城市车站查询
- 提供车站详细信息
- 智能解析查询意图

**使用示例:**
- "北京有哪些火车站"
- "上海的主要火车站是哪个"
- "查询北京南站的车站编码"

### 4. smart_travel_suggestion - 智能出行建议
综合分析直达和中转方案，根据用户偏好提供个性化出行建议。

**特点:**
- 综合分析多种出行方案
- 根据偏好推荐最优方案
- 提供详细的利弊分析
- 支持时间和价格优化
- 个性化推荐理由

**使用示例:**
- "从北京到上海怎么去最好"
- "给我推荐一下从广州到深圳的出行方案"
- "我想要最快的方案去杭州"

## 功能概览

### 车站信息查询
- **城市车站查询**: 查询指定城市的所有火车站
- **车站编码查询**: 获取车站的12306编码
- **车站名称查询**: 根据车站名称获取详细信息
- **主要车站识别**: 自动识别城市的主要车站

### 火车票查询
- **直达车票查询**: 查询两地之间的直达列车
- **票价信息**: 显示各种座位类型的价格和余票情况
- **车次筛选**: 支持按车型、时间等条件筛选
- **排序功能**: 支持按出发时间、价格等排序

### 中转方案查询
- **智能中转**: 自动计算最优中转方案
- **中转时间**: 显示换乘等待时间
- **中转车站**: 支持指定中转车站
- **全程时长**: 计算包含中转的总旅行时间

### 实用功能
- **日期管理**: 获取当前日期，支持相对时间查询
- **票量状态**: 实时显示余票情况
- **特殊标记**: 显示列车特性（如卧铺、餐车等）

## 原子工具（开发者接口）

原子工具提供了底层的技术接口，适用于系统集成和二次开发。每个原子工具实现单一功能，需要精确的参数输入。

### 基础信息工具

#### get_current_date - 获取当前日期
获取当前日期（上海时区）。

**参数:**
无

**使用场景:**
- 确认当前日期
- 相对时间计算
- 日期验证

#### get_stations_in_city - 获取城市车站
获取指定城市的所有火车站信息。

**参数:**
- `city` (必需): 城市名称

**使用场景:**
- 查看城市所有车站
- 选择具体车站
- 了解车站分布

#### get_city_station_code - 获取城市主要车站编码
获取城市主要车站的编码信息。

**参数:**
- `cities` (必需): 城市名称，多个城市用"|"分隔

**使用场景:**
- 快速获取主要车站
- 批量查询城市车站
- 系统集成

#### get_station_by_name - 根据车站名查询
根据车站名称获取详细信息。

**参数:**
- `station_names` (必需): 车站名称，多个车站用"|"分隔

**使用场景:**
- 验证车站名称
- 获取车站详细信息
- 车站信息确认

#### get_station_by_code - 根据车站编码查询
根据车站编码获取车站信息。

**参数:**
- `station_code` (必需): 车站编码

**使用场景:**
- 编码反查车站
- 系统数据验证
- 技术集成

### 2. 火车票查询工具

#### query_train_tickets - 查询火车票
查询指定日期和区间的火车票信息。

**参数:**
- `date` (必需): 出发日期，格式 "YYYY-MM-DD"
- `from_station` (必需): 出发车站
- `to_station` (必需): 到达车站
- `train_filters` (可选): 车次筛选条件
- `sort_by` (可选): 排序方式
- `reverse` (可选): 是否倒序
- `limit` (可选): 结果数量限制

**使用场景:**
- 日常出行查票
- 票价比较
- 出行规划

#### query_transfer_tickets - 查询中转车票
查询需要中转的火车票方案。

**参数:**
- `date` (必需): 出发日期
- `from_station` (必需): 出发车站
- `to_station` (必需): 到达车站
- `middle_station` (可选): 指定中转车站
- `show_wz` (可选): 是否显示无座
- `train_filters` (可选): 车次筛选条件
- `sort_by` (可选): 排序方式
- `reverse` (可选): 是否倒序
- `limit` (可选): 结果数量限制，默认10

**使用场景:**
- 无直达车时查询中转
- 比较中转方案
- 复杂出行规划

#### query_train_route - 查询车次经停站
查询指定车次的经停站信息。

**参数:**
- `train_code` (必需): 车次号

**使用场景:**
- 了解车次路线
- 选择中间站点
- 出行路线规划

注：此功能正在开发中

## 使用示例

### 基础信息查询示例

```python
# 获取当前日期
result = await mcp_server.call_tool("get_current_date", {})

# 查询北京的所有车站
result = await mcp_server.call_tool("get_stations_in_city", {
    "city": "北京"
})

# 获取多个城市的主要车站
result = await mcp_server.call_tool("get_city_station_code", {
    "cities": "北京|上海|广州"
})

# 根据车站名称查询
result = await mcp_server.call_tool("get_station_by_name", {
    "station_names": "北京南|上海虹桥"
})

# 根据车站编码查询
result = await mcp_server.call_tool("get_station_by_code", {
    "station_code": "VNP"
})
```

### 火车票查询示例

```python
# 基础火车票查询
result = await mcp_server.call_tool("query_train_tickets", {
    "date": "2025-07-15",
    "from_station": "北京",
    "to_station": "上海"
})

# 带筛选条件的查询
result = await mcp_server.call_tool("query_train_tickets", {
    "date": "2025-07-15",
    "from_station": "北京",
    "to_station": "上海",
    "train_filters": "G,D",  # 只查高铁和动车
    "sort_by": "departure_time",
    "limit": 10
})

# 中转车票查询
result = await mcp_server.call_tool("query_transfer_tickets", {
    "date": "2025-07-15",
    "from_station": "北京",
    "to_station": "广州",
    "limit": 5
})

# 指定中转站查询
result = await mcp_server.call_tool("query_transfer_tickets", {
    "date": "2025-07-15",
    "from_station": "北京",
    "to_station": "广州",
    "middle_station": "郑州",
    "limit": 5
})
```

## 数据结构

### 车站信息 (Station)
```python
{
    "station_code": "VNP",
    "station_name": "北京南",
    "station_pinyin": "beijingnan",
    "city": "北京",
    "code": "VNP"
}
```

### 火车票信息 (Ticket)
```python
{
    "start_train_code": "G1",
    "from_station": "北京南",
    "to_station": "上海虹桥",
    "start_time": "09:00",
    "arrive_time": "14:28",
    "duration": "5:28",
    "prices": [
        {
            "seat_name": "商务座",
            "price": "1748",
            "num": "3"
        },
        {
            "seat_name": "一等座",
            "price": "933",
            "num": "有"
        }
    ],
    "features": ["WiFi", "充电插座"]
}
```

### 中转方案 (Transfer)
```python
{
    "start_date": "2025-07-15",
    "start_time": "08:00",
    "arrive_date": "2025-07-15",
    "arrive_time": "20:30",
    "from_station_name": "北京南",
    "middle_station_name": "郑州东",
    "end_station_name": "广州南",
    "same_train": false,
    "same_station": true,
    "wait_time": "2小时15分",
    "duration": "12小时30分",
    "ticket_list": [
        {
            "start_train_code": "G79",
            "from_station": "北京南",
            "to_station": "郑州东",
            "start_time": "08:00",
            "arrive_time": "11:15",
            "duration": "3:15",
            "prices": [...]
        }
    ]
}
```

## 票量状态说明

### 余票显示
- **具体数字**: 如"5"表示剩余5张票
- **"有"**: 有票，具体数量不明
- **"充足"**: 票量充足
- **"无"**: 无票
- **"--"**: 该座位类型不可售
- **"候补"**: 无票，可候补

### 座位类型
- **商务座**: 最高等级座位
- **一等座**: 高等级座位
- **二等座**: 标准座位
- **无座**: 站票
- **硬卧**: 硬卧铺
- **软卧**: 软卧铺
- **高级软卧**: 豪华卧铺

## 查询技巧

### 1. 车站名称
- 使用官方车站名称，如"北京南"而不是"北京南站"
- 支持城市名称，系统会自动匹配主要车站
- 大车站可能有多个候选，建议具体到站名

### 2. 时间格式
- 日期格式：YYYY-MM-DD，如"2025-07-15"
- 支持相对时间，如"明天"、"后天"
- 注意节假日和调休安排

### 3. 筛选条件
- 车次筛选：G(高铁)、D(动车)、C(城际)、Z(直达)、T(特快)、K(快速)
- 时间筛选：可按出发时间或到达时间排序
- 价格筛选：可按票价高低排序

### 4. 中转查询
- 优先使用主要枢纽站中转
- 注意中转时间，建议预留充足换乘时间
- 考虑行李和出行便利性

## 注意事项

1. **数据实时性**: 票务信息实时更新，查询结果仅供参考
2. **购票渠道**: 工具仅提供查询功能，购票需通过官方渠道
3. **网络依赖**: 查询需要网络连接到12306系统
4. **查询限制**: 避免频繁查询，遵守12306使用规范

## 故障排除

### 常见问题
1. **车站名称错误**: 检查车站名称是否正确
2. **查询无结果**: 确认日期和车站信息
3. **网络超时**: 检查网络连接状态
4. **数据格式错误**: 验证输入参数格式

### 调试方法
1. 先查询车站信息确认车站名称
2. 使用get_current_date确认日期格式
3. 检查网络连接和防火墙设置
4. 查看返回的错误信息

## 二次开发指南

### MCP 工具集成

Railway工具基于MCP（Model Context Protocol）架构，支持灵活的工具集成和扩展。

#### 工具管理器
```python
from src.mcp.tools.railway import get_railway_tools_manager

# 获取工具管理器实例
manager = get_railway_tools_manager()

# 初始化工具（在MCP服务器中调用）
manager.init_tools(add_tool, PropertyList, Property, PropertyType)
```

#### 自定义智能工具
开发者可以基于现有原子工具创建新的智能工具：

```python
async def custom_smart_query(self, args: Dict[str, Any]) -> str:
    """自定义智能查询工具"""
    # 解析用户输入
    query = args.get("query", "")
    
    # 调用原子工具
    client = await get_railway_client()
    result = await client.query_tickets(...)
    
    # 格式化输出
    return self._format_custom_result(result)
```

### 架构说明

Railway工具采用分层架构：
- **智能工具层**: 处理自然语言输入，用户友好
- **原子工具层**: 提供基础功能，技术精确
- **客户端层**: 与12306 API交互
- **数据模型层**: 定义数据结构

### 扩展建议

1. **添加新的智能工具**: 基于现有原子工具组合新功能
2. **优化查询逻辑**: 改进智能工具的处理算法
3. **增强数据格式**: 添加更多输出格式选项
4. **集成其他服务**: 结合其他交通工具信息

通过火车票查询工具，您可以方便地获取火车票信息，规划出行路线，是出行必备的实用工具。智能工具让日常使用更加便捷，原子工具为开发者提供了强大的集成能力。