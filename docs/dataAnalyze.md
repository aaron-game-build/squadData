# 一、机器人相关

## 1.获取机器人的数量

```c++
int robotsNum = mapper[0][0]
```

## 2.获取所有机器人信息

```c++
vector<Robot> robots;

// 解析机器人
for (int i = 0; i < robotsNum; i++) {
  vector<int> robot = value[i];
  Robot r = {robot[0], robot[1], robot[2], robot[3], robot[4],
             robot[5], robot[6], robot[7], robot[8], robot[9]};

  robots.push_back(r);
}
```

## 3.分别获取敌我的机器人信息

```c++
vector<Robot> myRobots;     // 我的机器人
vector<Robot> ememyRobots;  // 敌方机器人

// 解析机器人
for (int i = 0; i < robotsNum; i++) {
  vector<int> robot = value[i];
  Robot r = {robot[0], robot[1], robot[2], robot[3], robot[4],
             robot[5], robot[6], robot[7], robot[8], robot[9]};

  robots.push_back(r);

  if (r.playerIndex == id) {
    myRobots.push_back(r);
  } else {
    ememyRobots.push_back(r);
  }
}
```

## 4.获取当前可行动的机器人（王国守卫战模式等于玩家拥有的所有机器人）

```c++
vector<int> actionableIndexList = value[robotsNum];
vector<vector<int>> actionableRobots;

unordered_set<int> actionableSet(actionableIndexList.begin(), actionableIndexList.end());

for (const auto& robot : robots)
{
    if (robot[0] == 0 && actionableSet.find(robot[1]) != actionableSet.end())
    {
        actionableRobots.push_back(robot);
    }
}
```

# 二、回合相关

## 1.获取全局的 round 数

```c++
int round = value[robotsNum + 5][0]
```

## 2.获取玩家的turn数

```c++
int turn = value[robotsNum + 6][0]
```

