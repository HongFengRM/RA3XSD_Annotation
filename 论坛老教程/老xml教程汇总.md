# 这里单纯复制了过来，单纯是为了搜索方便
红警 3 MOD 制作教程：红警 3 源代码详解
编写：
红警 DIY 论坛 ：yangqs
目录
1 基本代码详解
1. KindOf 详解
2. 装甲类型详解
3. 武器类型详解
4. 运动类型详解
5. 起义时刻 CSF 建筑和部队名称
6. 起义时刻 CSF 技能名称
7. 起义时刻 CSF 支援(机密)技能名称
8. 用写字板对 W3X 模型初解
9. OCL 产生新物体的重要参数
基本代码详解
<Includes>……</Includes> 对模型特效文件进行载入
<GameObject……</GameObject> 代码区
<Draws> ……</Draws> 代码区的一部分，属于模型与代码的结合区段
<Behaviors>……</Behaviors> 行为，代码区的一部分
下面对代码区的简单代码进行解释，这里，不包括<Draws>和<Behaviors>区段的内容
简单代码：
id="AlliedCommandoTech1" 标记，其他地方可以调用
EditorName="AlliedCommandoTech1" ai 建造名，在 AlliedBaseStates.xml 调用，一定要一
致
inheritFrom="BaseInfantry" 父级继承，就是继承了父级的某些特性，比如父级
"BaseInfantry"如果具有间谍的特性，那么将会遗传下来,需要<Includes>调用
IsTrainable="false"是否可训练，一般用于不升级的单位
SelectPortrait="Portrait_AlliedCommandoTech1_02" 肖像，点击该单位后，右下角所显示
的图像
ButtonImage="Button_AlliedCommandoTech1_on_02" 按键图像
Side="Allies" 阵营
SubGroupPriority="210" 子组优先级
Description="Desc:AlliedCommandoTech1" csf 解释,比如"一名使用双自动手枪和炸药，可
歼灭小规模军队的举世无双的女士兵。"
TypeDescription="Type:AlliedCommandoTech1" csf 类型解释，比如属于"突击队员"
UnitIntro="Allied_Tanya_UnitIntro"单位介绍，连接小视频 查找 UnitIntros.xml
HealthBoxHeightOffset="35" 健康盒，大概指三级的自我修复能力
BuildTime="30" 建造时间，如果是建筑，指菜单内的时间，如盟军的建筑
JustBuiltTime=1.5 战死后复活的时间，不能用于遭遇战
EnergyProduction="-25"建筑供应电量，负值为消耗电量
CommandSet="AlliedCommandoTech1CommandSet" 按键排列顺序，id 在
CommandSet.xml 排列顺序
KindOf=" CAN_BE_FAVORITE_UNIT" 个体 AI 及被操作的属性，以后详解
ThreatLevel="10" 恐吓级别，适用于载具和士兵
RadarPriority="STRUCTURE"雷达优先权
PlacementViewAngle="225d"建筑布置时方位角度
CampnessValue="=$CAMPNESS_DEFENSIVE_STRUCTURE"用于防御建筑，注意，=$代表
常量
SelectPortraitTransformed="Portrait_JapanAntiInfantryVehicle_jet"变形后的肖像
ButtonImageTransformed="Button_JapanAntiInfantryVehicle_jet"变形后的按键图像
DescriptionTransformed="Desc:JapanAntiInfantryVehicle_air"变形后的 csf 解释
TypeDescriptionTransformed="Type:JapanAntiInfantryVehicle_air"变形后的 csf 类型解释
BuildPlacementTypeFlag="OTHER_STRUCTURE"建筑安置类型，只有两个值，另一个是
"MAIN_STRUCTURE"
WeaponCategory="GUN" 单位所用武器范畴，只有 3 种，另两个是"CANNON"，
"MISSILE"，真正的武器很多，但不是这里
VoicePriority="120" 声音优先权，120 是英雄单位的
UnitTypeIcon="CommandoIcon"图标类型，就是小图标，比如“骷髅头像”“狗的头像”，在
UnitTypeIcons.xml
MaxSimultaneousOfType="1"同一时刻只能产生 1 个
Scale="0.8"在游戏里模型缩小 0.8，注意 OBBOX 不会缩小，而且缩小光束攻击后，将会把
模型打成原型比例
EditorSorting="UNIT" 类型，具体数值如下：
"SYSTEM" 系统单位，比如铁幕光效，被召唤的轰炸机等
"MISC_MAN_MADE"普通中立人群
"UNIT" 载具单位
"STRUCTURE" 建筑单位
"CAMPAIGN_UNITS"任务载具单位
"OBSOLETE"过时单位，好像没用，只有 3 个文件是这个属性 BaseCargo.xml ，
GUKoi01.xml，DestLight_01.xml
"MISC_NATURAL"普通中立单位
"OPTIMIZED_PROPS"最优化工具单位，好像用于地面等不可破坏的物体
"DESTRUCTIBLE_PROPS"易毁坏的工具单位，桥梁？
"AUDIO" 声音单位，只在 AudioAmbients.xml 有这个属性，是个特殊单位
ProductionQueueType="OTHER_STRUCTURE"生产序列类型，就是由哪个建造厂生产，具
体值如下：
"MAIN_STRUCTURE"主要建筑序列
"OTHER_STRUCTURE"防御建筑序列
"WATERCRAFT"船序列
"AIRCRAFT"飞行器序列
"VEHICLE"车辆序列
"INFANTRY"士兵序列
UnitCategory="INFANTRY"生产种类，具体值如下：
"VEHICLE"载具
"AIRCRAFT"飞机
"INFANTRY"生物
"STRUCTURE"建筑
>
=================
<EquivalentTo>JapanSuperWeaponAdvanced</EquivalentTo>等价单位，可以将两个毫
不相干的单位关联一起，比如某单位限制为 1，纳米车和建筑之间的关联
=================
<Define name="SOVIET_BASE_DEFENSE_GROUND_LOCAL_UNPACK_TIME" value="20s"
/> 建筑建造时间，指在菜单外的时间，如苏俄的建筑
</Defines>
=================
<DisplayName Name:AlliedCommandoTech1</DisplayName> csf 名，比如“谭雅”
=================
<DisplayNameTransformed
xai:joinAction="Replace"
xmlns:xai="uri:ea.com:eala:asset:instance">Name:JapanAntiInfantryVehicle_air</Displa
yNameTransformed>变形后的 csf 名，比如“天狗战机”
=================
<GameDependency>
<NeededUpgrade>Upgrade_AlliedTech3</NeededUpgrade> 建造时所需级别，比如谭雅
需要 3 级的主基地
<RequiredObject>AlliedTechStructure</RequiredObject>建造时所需的建筑，比如“高科”，
如果要电厂和矿场两个，就并列写两个<RequiredObject>
</GameDependency>
=================
<ObjectResourceInfo>
<BuildCost Account="=$ACCOUNT_ORE" Amount="2000"/>建造价格 2000，
"=$ACCOUNT_ORE"是常量，可能会受到机密武器的影响
</ObjectResourceInfo>
=================
<ArmorSet 装甲类型，以后详解
Armor="BaseCommandoArmor"
DamageFX="InfantryDamageFX" /> 受伤特效
=================
<LocomotorSet
Locomotor="TestReactiveLocomotorHUMAN" 运动类型，以后详解
Condition="NORMAL" 条件，当有多个装甲（速度，武器等）时，将会用 Condition 区分
如何使用
Speed="55" /> 速度
=================
<SkirmishAIInformation 遭遇战 AI 信息
UnitBuilderStandardCombatUnit="true" 是否是基础兵
UnitBuilderStandardCombatUnit="true" 标准化作战部队
ConquerMetricsOverrideDPS="100" 自动控制级别
ConquerMetricsOverrideDamageType="AUTO_CANNON" 目前未知
ConquerMetricsOverrideAntiMask="ANTI_WATER
ANTI_GROUND ANTI_STRUCTURE" 目前未知
BaseBuildingLocation="NEAR_RESOURCE_NODE"此建筑一般建在哪里，数值如下
"BACK" 阵地后方
"FRONT"阵地前方
"DEFENSE" 防御附近
"CENTER"阵地中心
"SPREAD"散布四周
"NEAR_RESOURCE_NODE"矿源附近
NearResourceNodeType="ORE">矿源类型，仅此一个值
<ResourceNodeBaseClosenessTestSelectionCriteria 用于矿场选择标准
PreferredNotBaseTypes="CAPTURED"首选的非标准类型，矿场首选是被占领类型，其他
次之
SortOrder="PREFER_CLOSEST" />类别顺序
</SkirmishAIInformation>
=================
<ConstructionBaseSelectionCriteria 建筑选择标准
ExcludedBaseTypes="NO_BUILD_RADIUS CAPTURED"不包括的类型
PreferredBaseTypes="MAIN_BASE"首选的标准类型
SortOrder="PREFER_OLDEST" />类别顺序
OutOfRangePenalty="30.0"/> 遭遇战 AI 信息
这里说一下首选标准类型，PreferredNotBaseType，PreferredBaseType 的具体值如下：多
选
"MAIN_BASE"主要基础类型
"ENEMIES_IN_BASE” 敌人基地类型
"UNDER_ATTACK"被攻击类型
"CAPTURED"被占领类型
"NO_BUILD_RADIUS"无建造半径类型，例如日本的蜂房
=================
<AI>个体行为 AI 默认设置，不适合于建筑
<AIUpdate
id="ModuleTag_AI"
AutoAcquireEnemiesWhenIdle="YES"空闲时是否自动察觉敌人
StateMachine="UnitAIStateMachine">国家机器
<UnitAITargetChooserData
CanPickDynamicTargets="true"可以动态攻击目标
IdleScanDelay= "1.0s" />空闲时扫描延迟，填写秒数，貌似最大为 1 秒，越大越迟钝
</AIUpdate>
</AI>
=================
<Body>
<ActiveBody
id="ModuleTag_Body" MaxHealth="300" /> 生命值
</Body>
=================
<Geometry 几何体，如果受到攻击，将会根据这里的攻击范围进行判断
IsSmall="true"> 是否是小型物体
<Shape
Type="CYLINDER" 类型，将人物设为圆柱体，坦克和建筑为"BOX"
MajorRadius="7.0" 半径
Height="13.0" 高度
ContactPointGeneration="SQUAD_MEMBER"/> 产生联系点，有 4 个值
"STRUCTURE" 建筑
"VEHICLE" 车辆
"SQUAD_MEMBER"小组成员，英雄是这个选项
"INFANTRY" 士兵
</Geometry>
=================
<ClientBehaviors>客观行为
<ModelConditionAudioLoopClientBehavior id="ModuleTag_ShrunkenVoice">
<ModelConditionSound Sound="SOV_V4_VoiceShrunken"
RequiredFlags="SHRINK_EFFECT" />
</ModelConditionAudioLoopClientBehavior>
<ModelConditionSoundSelectorClientBehavior
id="ModuleTag_SOV_V4_VoiceAttackSpecial">
<Override RequiredFlags="USER_6">
<AudioArrayVoice>
<AudioEntry Sound="SOV_V4_VoiceAttackSpecial" AudioType="voiceAttack" />
</AudioArrayVoice>
</Override>
</ModelConditionSoundSelectorClientBehavior>
</ClientBehaviors>
=================
<AudioArrayVoice>声音队列
<AudioEntry Sound="SOV_V4_VoiceAttack" AudioType="voiceAttack" />
<AudioEntry Sound="SOV_V4_VoiceCreate" AudioType="voiceCreated"
/>
<AudioEntry Sound="SOV_V4_VoiceMove" AudioType="voiceMove" />
<AudioEntry Sound="SOV_V4_VoiceMoveAttack"
AudioType="voiceAttackAfterMoving" />
<AudioEntry Sound="SOV_V4_VoiceRetreat"
AudioType="voiceRetreatToCastle" />
<AudioEntry Sound="SOV_V4MissileLauncher_VoiceSelectMS"
AudioType="voiceSelect" />
<AudioEntry Sound="SOV_V4_VoiceSelectBattleMS"
AudioType="voiceSelectBattle" />
<AudioEntry Sound="SOV_V4_VoiceSelectUnderFireMS"
AudioType="voiceSelectUnderFire" />
</AudioArrayVoice>
<AudioArraySound>音乐队列
<AudioEntry Sound="SOV_V4_Land_MoveLoopMS"
AudioType="soundMoveLoop" />
<AudioEntry Sound="SOV_V4MissileLauncher_MoveStart"
AudioType="soundMoveStart" />
<AudioEntry Sound="SOV_V4MissileLauncher_IdleLoop"
AudioType="soundAmbient" />
<AudioEntry Sound="VehicleCrush" AudioType="soundCrushing"
/>
</AudioArraySound>
其中 AudioType=数值如下：
"voiceAttack"进攻的声音
"voiceCreated"建造的声音
"voiceMove"移动的声音
"voiceAttackAfterMoving"攻击后移动的声音
"voiceRetreatToCastle"撤出碉堡的声音
"voiceSelect"选择的声音
"voiceSelectBattle"优势作战时，选择的声音
"voiceSelectUnderFire"在战火中选择的声音
"voiceAttackUnit"进攻单位的声音
"soundMoveStart"开始移动的声音
"soundCrushing"碾压的声音
"soundMoveLoop"移动的循环声音
"soundTurretMoveLoop"炮塔移动的声音
"soundAmbient"环境声音
=================
<EvaEventArray> 伊娃事件
<EvaEntry EvaEvent="TanyaLost" 事件=被打死
EvaType="dieOwner" /> 类型= dieOwner 声音
<EvaEntry EvaEvent="EnemyCommandoDetected"
EvaType="enemyObjectSighted" />
</EvaEventArray>
=================
<ShadowInfo 阴影信息，好像只适用于步兵
Type="DECAL" 类型=贴花纸，还有"ADDITIVE_DECAL"
SizeX="14"
SizeY="14"
Texture="ShadowI" />阴影的图案纹理
=================
<VisionInfo 可视信息
VisionRange="200" 可视范围，防御范围
ShroudClearingRange="500" /> 清除灰雾的范围
=================
<CrusherInfo 被压信息，不适用于建筑
id="id_CrusherInfo"
CrusherLevel="0" 压碎者级别
CrushableLevel="50"被压者级别，谭雅 50 不被碾压，天启才 30
CrushEqualLevelProps="true"是否有碾压同等水平道具
CrushAllies="true"是否碾压盟友
CrushWeapon="SovietCrushWeapon"碾压的武器
CrushDecelerationPercent="80%" />碾压时减速
=================
<;ProjectedBuildabilityInfo 建筑扩展面积，在扩展范围里可以建造防御塔等
Radius="240"
RadiusY="255"如果是方形，可以不用写此参数
BuildPlacementTypes="MAIN_STRUCTURE OTHER_STRUCTURE" />可允许放置的建筑类
型，似乎怎么改都没用，主建筑和防御建筑总是有效
KindOf 详解
上文所提到的 KindOf =最复杂，可以在每个单位都能看到，是个体 AI 及被操作的属性，
可以多选
IncludeKindOf 与 ExcludeKindOf 的值应该和 KindOf 是一样的，不过 IncludeKindOf 与
ExcludeKindOf 应该属于攻击敌人的 AI 过滤器，放在"BalancedStates.xml"里面，专用于遭
遇战的 AI
VitalKindOf 与 ForbiddenKindOf 又是一对冤家（一个是紧要，一个是禁要），放在
"AITargetHeuristicLibrary.xml"里面，直译，这个文件是 AI 目标启发库
还是先和大家说说 KindOf，具体数值如下：
UNIQUE_UNIT 屏蔽掉 shift+左键的建造功能
+UNIQUE_UNIT 同第一条，屏蔽掉 shift+左键的建造功能，竟然用于超级武器，光棱塔等
NOT_AUTOACQUIRABLE 不能自动获得，有很多后台的东西都用这个参数，但最直观的是
日本的气球炸弹等机密武器
+NOT_AUTOACQUIRABLE 不能自动获得，有+，说明是用于非中立的建筑的，一般用于某
些墙体建筑
-NOT_AUTOACQUIRABLE 自动获得，有-，在沿海巨炮里出现过此代码。（-NOT——似乎
可以翻译成不得不），”-”代表去掉父级的这个参数
SMALL_MISSILE 属于小型导弹
DEFLECT_BY_SPECIAL_POWER 可被黑洞装甲吸引，一般指 射弹 物体
NO_COLLIDE 无碰撞 常用于射弹
HIDE_IF_FOGGED 有雾将会隐藏
INERT 惰性，有很多后台的东西都用这个参数，但最直观的是日本的气球炸弹，或者其他
爆炸物
UNATTACKABLE 不能主动进攻，有很多后台的东西都用这个参数，但最直观的是日本的气
球炸弹
INERT_SHROUD_REVEALER 苏俄的辐射炸弹，磁力特效，铁幕特效用此参数，应该是对
灰雾有一定的探测作用，而探测的范围只局限于光效本身，换句话说，在黑雾中能看到这
种光效
PASS_EXPERIENCE_TO_PRODUCER
SKIRMISH_AI_ATTEMPT_TO_DODGE
SIMPLE_OBJECT_PROP
ALWAYS_COLLIDE_WITH_OWN_SHIELD_SPHERES
IMMOBILE 稳定，貌似不移动（固定）的意思
+IGNORE_FOR_VICTORY 面对胜利不理睬，用过此代码的建筑，是和游戏胜负的判断毫无
相关的，比如各种防御单位都有此代码，你不消灭它们，只消灭主基地就会赢
CANNOT_BE_DETECTED 不被察觉，看来是间谍类
RESIST_EMP 抵抗 EMP，EMP 对它无效
+SUMMONED 被召唤的建筑，如时空炸弹
SUMMONED 被召唤，如日本的敢死队等各种机密武器
DRONE 雄蜂，只有美国地图探测者用这个参数，大概是地图探测者的专属
NO_SHADOW 没有阴影，常用于导弹
+AIRFIELD 属于机场建造单位
+FS_FACTORY 属于工厂建筑
+FS_AIR_FIELD 属于机场建筑
+FS_TECHNOLOGY 属于高科技建筑
+FS_WAR_FACTORY 属于战车工厂建筑
+FS_BARRACKS 属于兵营建筑
+CAN_ATTACK 可以自主攻击
+CONSTRUCTION_YARD 属于主基地类型
+FS_BASE_DEFENSE 属于防御建筑
+CRANE 属于起重机类型
+OUTPOST 属于分属指挥中心单位
+FS_POWER 属于电厂建筑
+SUPPLY_GATHERING_CENTER 补给中心
+FS_MONEY_STORAGE 储钱容器
+REFINERY 就是矿场，一般矿场都具备以上 3 个参数，不知道分别单独使用会怎样，难
道会有虽有补给中心，但就是存不住钱的道理？
+REVEAL_TO_ALL 暴露于天下，主要用于各种超级武器，如果觉得不够刺激，可以去掉，
玩的时候到处找不到敌人的超武，呵呵
+SUPER_WEAPON 是超级武器
STRUCTURE 属于建筑类型
VEHICLE 属于车辆类型
SHIP 属于船只类型
PROJECTILE 属于射弹物体
AIRCRAFT 航行器，就是天上飞的，包括飞行兵
ASSAULT_AIRCRAFT 可以防空
CAN_BE_FAVORITE_UNIT 招人喜欢的单位，什么意思？日本单位常用
LIMITED_PRODUCTION_AIRCRAFT 此单位的数量受到机场机位的限制
INFANTRY 属于步兵类型
TRANSPORT 属于运输单位
AMPHIBIOUS 属于两栖类型
SKIRMISH_AI_DONT_REPAIR 遭遇战中 AI 不会维修，例如狗
+POWERED 耗电建筑，电力不足时将会瘫痪
+POWERED_POWERS_ONLY 只能消耗电厂供应的电，主机无法给它供电？
+AUTO_RALLYPOINT 集结点，生产建筑都有此参数
CAN_BUILD_ON_WATER 可以建在水中
CAN_BUILD_ON_DEEP_WATER 可以建在深水中，通常和上一条配合使用
+CAN_NOT_BUILD_ON_LAND 不能建在陆地上
+GARRISONABLE_UNTIL_DESTROYED
CAN_SEE_THROUGH_STRUCTURE 可以看“穿”建筑
+LINE_OF_SIGHT_IGNORES_BUILDINGS 一般用于光棱塔，磁暴线圈，忽略建筑直视某地
区
LINE_OF_SIGHT_IGNORES_BUILDINGS 一般用于防空兵，忽略建筑直视某地区
SELECTABLE 可被玩家选择
T2_UNIT 是否定义为第二科技单位
T3_UNIT 是否定义为第三科技单位
COMMANDO 是否定义为英雄单位
ENGINEER 是否定义为工程师
FIGHTER_AIRCRAFT 是否定义为战斗机
INFILTRATOR 是否定义为渗透者，间谍
EXPANSION_UNIT 是否定义为扩展单位，包括主基地和分基地
MCV 是否定义为基地车
HARVESTER 是否定义为收割者，用于矿车
BRIDGE 是否定义为是桥梁
CAN_CAPTURE 是否可以占领敌人建筑物
FS_BASE_DEFENSE 用于防御核心
-PROJECTILE 非射弹类型，而是燃烧的流星式
+GARRISON 驻防要塞，比如苏俄的碉堡
GARRISON 要塞，用于中立建筑
SUPER_WEAPON 超级武器
+FS_TECH_CENTER 是否是科技中心
FS_TECHNOLOGY
OBSTACLE 是否是障碍物
TIME_BOMB 是否是定时炸弹
ENCLOSURE 是否是围墙
WALL_PIECE 是否是墙片
TRANSFORMER 是否是变形者
SUBMARINE 是否是潜水艇
SNIPER 是否是狙击手
DEBRIS 是否定义为碎片
NEUTRAL_TECH 是否是中立科技单位
CAPTURABLE 是否是是战利品，是否可被工程师占领
ARMY_SUMMARY 军队，是否是一群人
CIVILIAN_UNIT 是否是 中立单位
CAN_CAST_REFLECTIONS
AUTO_ACQUIRABLE_BY_AI
COVER 貌似是附属建筑的重要参数，看来仍然保留了某些 CNC3 的功能
SCORE 应该是此单位被苏俄的“R”砸到，死后会返钱给敌人，如果没有这个参数，砸了也
白咋，据“從欣來過”说也关联着死亡计数，需要<Physics id="ModuleTag_Physics" />配合
+ACTIVATE_AFTER_UNPACK 展开好后才工作，这是典型的苏俄建筑，盟军是没有造好建
筑就可以里面的步兵坦克，其实盟军建筑有 2 秒的建造时间，但没有这个参数，所以 2 秒
被忽略
+SKIRMISH_AI_CAN_BUILD_DURING_EMERGENCY_NO_INCOME 遭遇战中 AI 可以在资
金紧张或没有收入的时候建造，用于建筑，如电厂，矿场，属于电脑作弊代码
SKIRMISH_AI_CAN_BUILD_DURING_EMERGENCY_NO_INCOME 遭遇战中 AI 可以在资金
紧张或没有收入的时候建造，如矿车，基地车
CAN_ATTACK 可以攻击
CANNOT_HIJACK 不被抢劫，各个动物和蜘蛛专用，可能是不被间谍花钱买通
NO_GARRISON 默认不会驻守，会被敌人诱杀
PRELOAD 预载，貌似多用于中立建筑，过多的单位加入预载，很可能减慢载入游戏的时间
（不过游戏过程中会加速）
SIEGE_WEAPON 属于攻城用武器，一般把超重型武器定义为这个，如日本的幕府战舰，以
后 AI 好调用或者避开
DISGUISER 伪装者,用于幻影和间谍
SKIP_IDLE_WHEN_CAPTURED 当被敌人俘获后，跳过空转（IDLE），用于维修的小机器
人
BOMBER_AIRCRAFT 轰炸机航天器，比如基诺夫，世纪轰炸机
AIRCRAFT_TRANSPORT_ONLY_GARRISONABLE_WHILE_PARKED 只能在基地进行载人，
比如世纪轰炸机
SKIRMISH_AI_DONT_GARRISON 遭遇战中此单位的 AI 不进行防守
IGNORE_FORCE_MOVE 忽略力场移动
CAN_PLACE_CHARGE
IGNORES_SELECT_ALL 忽略圈选，当圈选时，此单位会漏掉，如矿车
CYCLE_SELECTION 循环选取
UNPACKS_INTO_BUILDING 展开成建筑
MOVE_FOR_NOONE 向无人区移动，用于矿车
SKIRMISH_AI_DONT_CONSIDER_THREAT
LEAVE_PARKING_ON_BUILD_COMPLETE
PRODUCED_AT_HELIPAD
DO_NOT_CLASSIFY 不分等级，不升级
ALWAYS_VISIBLE_IN_RADAR 雷达中总是可见，如中立建筑
KEEP_CLASSIFIED_WHEN_DEAD 消灭后保证分类的存在，用于中立单位
CIVILIAN_BUILDING 中立建筑
NOT_SELLABLE 不能变卖，找了半天，却没有不能维修的参数
+CRUSHABLE_BUILDING 可压碎的建筑，很奇怪，只用于苏俄的建筑
AUTO_RALLYPOINT 此建筑拥有自动集结点
WORLDBUILDER_SNAP_TO_GRID 吸附网格，用于断崖和路桥
CLEARED_BY_BUILD 可被建筑清除，例如树木和石头
ORE_NODE 矿石节 ， 用于矿石
IMMUNE_TO_CAPTURE 对占领免疫，比如钻矿井
CRUSHABLE_OBSTACLE 压碎障碍物
TERRAIN_LIKE_GROUND_OBJECT 地形象平地一样
OPTIMIZED_PROP 优化工具物
TIBERIUM_BASED
TIBERIUM 是否是泰伯利亚矿
CLASSIFY_ENTIRE_FOOTPRINT
ACTIVATE_AFTER_UNPACK 拆包后激活
HAS_HEALTH_BAR 拥有健康条
AI_CAN_UNPACK_NEAR_CONYARD
AIRCRAFT_PATH_AROUND
IGNORED_IN_FINDPOSITIONAROUND 忽视周围环境都能建造，如纳米蜂窝煤
CAN_NOT_BUILD_ON_LAND 陆地上不能建造
SKIRMISH_AI_DONT_MULTI_TARGET 遭遇战中，AI 没有多个目标，如蜻蜓，也只有蜻蜓
由此参数
BRIDGE_SEGMENT
BRIDGE_ENDCAP
BRIDGE_GATEHOUSE
PATH_THROUGH_INFANTRY 穿过人群，如磁力卫星的光效
CRUSH_CRUSHABLE_BUILDINGS 碾压，可以碾压建筑
DONT_DESTROY_IF_ON_BRIDGE 如果在桥上将不会受伤，例如鬼王
CRATE 箱子
PARACHUTABLE 降落伞，从天而降，用于维修的箱子
BEACON 灯塔照明
WB_DISPLAY_SCRIPT_NAME
OPTIMIZED_SOUND 优化声音
ALWAYS_VISIBLE 总是被看到，用于全局，如超武
+DONT_UNATTACH_WHEN_HEALING 治疗时不被攻击
NEVER_CULL_FOR_MP 从不精选，用于"ControlPoint.xml"控制点，这个最好不要改
+GRANTS_VETERANCY 同意部队升级，如果工程师占领此建筑，将会建出升级的兵种
AI_NEEDS_PLAYER_POWER_UPDATEAI 需要玩家电力升级？
SHOW_BEHIND_OCCLUDERS 显示背面遮光板，用于磁力卫星的特效
+PASS_EXPERIENCE_TO_PRODUCER 使用就会增加经验，应该是用于娜塔莎的支援轰炸
机上的炸弹
CARPET_BOMBER 是否是地毯式轰炸，用于基诺夫
DONT_SUBMERGE_BY_WAVES 不能被水淹没，目前只有苏俄的工程师 使用这个
ATTACH_ATTACK 蜘蛛的寄生攻击，应该还要有其他代码配合才对
+TRANSPORT 任务地图专用的一种运输
+NONOCCLUDING 不阻隔， 用于 ”SovietTeslaWallHub"(译为磁暴墙体 )
DRAWABLE_ONLY 只能点击，用于系统物体，集结点设置者或者玩家目标点设置者
SPELL_BOOK 魔法书，只用于 PlayerSpellBook.xml ， 用于机密武器和超级武器
HORDE 移动着的一大群，cnc3 常见，一大群共用一个血条
LARGE_RECTANGLE_PATHFIND 矩阵探路
=$FACTORY_REPAIR_DRONE_KINDOF 常量，具体代表什么需要查找"GlobalDefines.xml"，
一般有几个同等的值会用这个办法，因为一但修改一个值，那么所有的关联都被修改
装甲类型详解
装甲类型 Armor.xml
<ArmorTemplate
id=" BaseCommandoArmor "士兵或者建筑调用这个标签
inheritFrom="BaseABCDEFArmor">继承于下方
</ArmorTemplate>
<ArmorTemplate
id="BaseABCDEFArmor" > 各武器对这个装甲的作用
<Armor
Damage="SNIPER" 阻击枪
Percent="100" />装甲厚度
<Armor
Damage="CANNON"加农炮
Percent="20" />装甲厚度
<Armor
Damage="ROCKET"导弹
Percent="20" />
<Armor
Damage="GRENADE"手榴弹
Percent="100" />
<Armor
Damage="GUN"小兵的枪
Percent="100" />
<Armor
Damage="MELEE"格斗
Percent="100" />
<Armor
Damage="AUTO_CANNON"自动加农炮
Percent="150" />
<Armor
Damage="IMPACT"冲击波
Percent="100" />
<Armor
Damage="EXPLOSIVE"爆炸
Percent="100" />
<Armor
Damage="FLAK"高射炮
Percent="10" />
<Armor
Damage="PRISM"光棱
Percent="100" />
<Armor
Damage="TESLA"磁暴
Percent="1000" />
<Armor
Damage="RADIATION"辐射
Percent="100" />
</ArmorTemplate>
武器类型详解
武器类型 Weapon.xml
<WeaponTemplate……</WeaponTemplate>
id="SovietFighterAircraftFlakMissile"
AttackRange="200.0"攻击范围
MinimumAttackRange="10"最小攻击范围
WeaponSpeed="500"武器速度
AcceptableAimDelta="20d"武器横向角度，超过角度将不会射击，除非调整自
身的位置后再射击
PreAttackType="PER_SHOT"每次攻击类型，3 个值，分别为"PER_CLIP"弹夹，
"PER_SHOT"开枪，"PER_TARGET"目标
ClipSize="16"弹夹大小
AutoReloadsClip="RETURN_TO_BASE"自动换弹夹，3 个值，分别为"AUTO"自
动，"NONE"无，"RETURN_TO_BASE"返回出发点
Flags="ATTACK_NEEDS_LINE_OF_SIGHT NOT_ATTRACTED_BY_MAGNETS"
标志
FireSound="SOV_MigFighter_MissileFire"开枪的声音
FireFX="FX_SovietMigMissilesFire"开枪枪口特效
FireVeteranFX="FX_SovietMigMissilesFire_Vet"老兵开枪枪口特效
RequiredAntiMask="ANTI_AIRBORNE_VEHICLE ANTI_AIRBORNE_INFANTRY"
此武器对这些单位有效，多选，具体如下
ANTI_GROUND 对地面单位有效
ANTI_STRUCTURE 对建筑有效
ANTI_WATER 对水面单位有效
ANTI_SUBMERGED 对潜艇有效
ANTI_VEHICLE 对载具有效
ANTI_INFANTRY 对士兵有效
ANTI_AIRBORNE_VEHICLE 对空中载具有效
ANTI_AIRBORNE_INFANTRY 对空中士兵有效
ANTI_LIFTED_GROUND_UNIT 对腾空于地面的单位有效
ANTI_AIRBORNE_INFANTRY"对飞行器有效
ANTI_PARACHUTE 对伞兵有效
ANTI_PROJECTILE 对射弹有效
ANTI_SMALL_MISSILE 对小导弹有效
ANTI_BALLISTIC_MISSILE 对弹道导弹有效
ANTI_MINE 对矿山有效
ProjectileCollidesWith="ALLIES ENEMIES NEUTRAL STRUCTURES WALLS"发射对象=敌人
中立 盟友 建筑 墙体
CanFireWhileMoving="true"是否移动时可以进攻
InstantLoadClipOnActivate="true"
VirtualDamage="SHARE"虚拟伤害，3 个值，分别为"NONE"无，"SOLO"单独，
"SHARE"共享
RadiusDamageAffects="ENEMIES"伤害对象=ENEMIES 敌人， NEUTRALS 中立， ALLIES
盟友， SELF 自己
>
<PreAttackDelay 攻击之前停顿
MinSeconds="0.1s"
MaxSeconds="0.1s" />
<FiringDuration 开火持续时间
MinSeconds="0.1s"
MaxSeconds="0.3s" />
<ClipReloadTime 换弹时间
MinSeconds="0.3s"
MaxSeconds="0.5s" />
Flags= 标志，多选,分别如下：
NOT_ATTRACTED_BY_MAGNETS 此武器不被磁力卫星卷走
ATTACK_NEEDS_LINE_OF_SIGHT 此武器为需要可视攻击虚线的攻击
RELOAD_WHEN_ATTACK_STOPS 此武器攻击停止时需要重载
IGNORE_TARGET_AS_OBSTACLE 此武器为有障碍物时忽略目标
FORCE_EMPTY_ENTIRE_CLIP
+SYNC_AMMO_ON_ACTIVATE 此武器为弹药同步启动
CRUSH_VEHICLE 此武器为碾压
IGNORE_WALL_RELATIONSHIP 此武器可穿越墙体
IGNORE_ENCLOSURE_CHECK 此武器忽略围栏检查
<Nuggets>弹头，共分类 35 种
武器弹头类型中，在武器方面共有 35 种不同类型的弹头,分别如下：
<DamageNugget>杀伤类弹头，最终的伤害一般由这个起作用，比如一个[发射体弹头]所
携带的子弹头就是[杀伤弹头]
<DOTNugget>圆点弹头
<DamageAndSpawnNugget>杀伤和卵生弹头
<ProjectileNugget>发射体弹头,最为常见
<SuppressionNugget>抑制弹头
<TerrainCraterNugget>地形破坏弹头
<WeaponOCLNugget>武器建造列表弹头
<ActivateLaserNugget>启动激光弹头
<ActivateStreamNugget>启动队列弹头
<ActivateLiftObjectNugget>启动举起物件弹头
<ActivateLinearDamageNugget>启动线的杀伤弹头
<ActivateCircularDamageNugget>启动圆环的杀伤弹头
<SlavesAttackNugget>服从者攻击弹头，比如舰载机
<MetaImpactNugget>气浪弹头
<LeechHealthDamageNugget>吸血杀伤弹头，铁锤坦克用的就是这个弹头
<SecondaryDamageNugget>第二杀伤弹头，冷冻弹头
<SpecialPowerNugget>特别的能力弹头，技能弹头
<AttributeModifierNugget>属性修改弹头
<DamageContainedNugget 杀伤包含弹头
<LuaEventNugget>事件弹头
<LineDamageNugget>线性杀伤弹头
<SeedTiberiumNugget>播种泰伯利亚矿弹头
<ParalyzeNugget>麻痹弹头
<InformationWarfareNugget>战斗信息弹头
<SpendStolenTiberiumNugget>花费偷泰伯利亚矿弹头
<ReportWeaponFiredStatNugget>报告武器点燃了放射弹头
<ScatterProjectileNugget>散弹发射体弹头
<FireOnObjectsNugget>在物件弹头上点燃的弹头
<TintObjectsNugget>物体染色弹头，比如 C4 时，将敌人变红，辐射时，物体变绿
<ContainedObjectAttackNugget>包含物件攻击弹头
<InformTargetNugget>信息目标弹头
<AttachNugget>C4 缚上弹头
<StripMaxHealthPercentNugget>包含物件攻击弹头
<GrapplingHookNugget>互钩弹头
<LeechPercentMaxHealthDamageNugget>以吸血百分比最大健康杀伤弹头，比如百合子
下血方式
DamageType=杀伤类型，在<DamageNugget>杀伤类弹头里，具体数值如下：
"EXPLOSIVE"爆炸
"ROCKET"导弹
"KI"意念
"UNRESISTABLE"不抵抗
"SNIPER"狙击手，按照百分比下血
"MELEE"格斗
"GRENADE"手榴弹
"FLAK"高射炮
"MAGIC"魔术，吸血
"CONCUSSIVE"冲击波
"CANNON"炮轰
"PRISM"光棱
"AUTO_CANNON"自动火炮
"HEALING"医疗
"GUN"手枪
"TESLA"磁暴
"CRUSH"碾压
"RADIATION"幅射
DeathType=死亡类型，在<DamageNugget>杀伤类弹头里，具体数值如下：
NORMAL 正常死亡
EXPLODED 爆炸死亡
SHATTERED 坠落而死
STABBED 杀死
DETONATED 引爆而死（C4？）
CATALYST 催化而死
BITTEN 咬死?
LASERED 激光打死
ELECTROCUTED 电死
CRUSHED 压死
BURNED 烧死
SUICIDED 自杀
INTERNAL_DESTRUCTION 内在破坏而死（蜘蛛？）
IRRADIATED 辐射而死
运动类型详解
<LocomotorTemplate
id="ABCDEFLocomotorHUMAN"随意定义标签，但定义和调用要一致
Surfaces="GROUND"表面运动方式，下方会有详细的值
TurnTimeSeconds="0.5s" 转弯时速度
TurnTimeDamagedSeconds="0.5s"受伤时转弯时速度
FastTurnRadius="1.0"快速转弯时的半径
SlowTurnRadius="1.0"慢速转弯时的半径
AccelerationSeconds="0.0s"加速度
BrakingSeconds="0s" 减速度
FormationPriority="NO_FORMATION"编队优先权
MinTurnSpeed="0%"转速差，是否每次的转弯速度都不同，不同的比率
BehaviorZ="NO_MOTIVE_FORCE"Z 轴行为
Appearance="TWO_LEGS"外表=两条腿
StickToGround="true"是否接触地面
AirborneTargetingHeight="30"空中的目标高度
/>
其中
Surfaces= 表面运动方式多选，数值如下：
"GROUND"可在平地行走
"WATER"可以游泳
"DEEP_WATER"可以潜水
"CLIFF"可以攀岩
"AIR"可以飞行
"CRUSHABLE_OBSTACLE"可压碎障碍物
"CRUSHABLE_WALL"可压碎墙
例如"GROUND WATER"就是两栖
Appearance=外表，数值如下：
"HOVER"盘旋状，比如空袭的炸弹
"TWO_LEGS"双腿状，例如士兵，天狗的爬行，不会留下脚印
"SHIP" 船状，例如海豚
"TREADS"轮胎状，例如多功能步兵战斗车
"WINGS"飞翼状，如天翼
"FOUR_WHEELS"四轮状， 应该是履带状才对，各种履带车都用此参数
BehaviorZ=Z 轴行为，值得注意的是，此值的改变需要其他附属参数配合，数值如下：
"FLOATING_Z"漂浮的
"NO_MOTIVE_FORCE"无动力的
"SEA_LEVEL"海洋级别
"SURFACE_RELATIVE_HEIGHT"表面相对高度
"SEA_LEVEL_SMOOTH_Z"平滑级海洋级别
起义时刻 CSF 建筑和部队名称
NAME:ACTIVATEMIRAGEFIELD = 裂痕产生器
NAME:ABILITYREPAIRVEHICLE = 维修站
NAME:AIRPORTTECHBUILDING = 机场
NAME:ALLIEDAIRFIELD = 空军基地
NAME:ALLIEDANTIAIRSHIP = 水翼船
NAME:ALLIEDANTIAIRVEHICLETECH1 = 多功能步兵战斗车
NAME:ALLIEDANTIGROUNDAIRCRAFT = 维和轰炸机
NAME:ALLIEDANTIINFANTRYINFANTRY = 维和步兵
NAME:ALLIEDANTIINFANTRYVEHICLE = 激流 ACV
NAME:ALLIEDANTINAVALSCOUT = 海豚
NAME:ALLIEDANTINAVYSHIPTECH1 = 突袭驱逐舰
NAME:ALLIEDANTISTRUCTURESHIP = 航空母舰
NAME:ALLIEDANTISTRUCTUREVEHICLE = 雅典娜炮
NAME:ALLIEDANTIVEHICLEINFANTRY = 标枪兵
NAME:ALLIEDANTIVEHICLEVEHICLETECH1 = 守护者坦克
NAME:ALLIEDANTIVEHICLEVEHICLETECH3 = 幻影坦克
name:AlliedArtilleryVehicle = 平定者
NAME:ALLIEDBARRACKS = 新兵训练营
NAME:ALLIEDBASEDEFENSE = 多功能步兵炮塔
NAME:ALLIEDBASEDEFENSEADVANCED = 电磁波塔
NAME:ALLIEDBOMBERAIRCRAFT = 世纪轰炸机
NAME:ALLIEDCOMMANDOTECH1 = 谭雅
NAME:ALLIEDCONSTRUCTIONYARD = 建筑工厂
NAME:ALLIEDCRANE = 起重机
NAME:ALLIEDDISRUPTORSTATION = 传递站
NAME:ALLIEDENGINEER = 工兵
NAME:ALLIEDFIGHTERAIRCRAFT = 阿波罗战斗机
NAME:AlliedFutureTank = 未来坦克 X-1
name:AlliedGunshipAircraft = 先锋武装战艇机
NAME:ALLIEDINFILTRATIONINFANTRY = 间谍
NAME:ALLIEDLEGIONNAIREINFANTRY = 冰冻兵团
NAME:ALLIEDMARINE1 = 总统的直升机
NAME:ALLIEDMCV = MCV
NAME:ALLIEDMINER = 探矿车
NAME:ALLIEDNAVALYARD = 海港
NAME:ALLIEDNAVALYARDREPAIRBAY = 修护厂
NAME:ALLIEDOUTPOST = 指挥中心
NAME:ALLIEDPOWERPLANT = 发电厂
NAME:ALLIEDPOWERPLANTTURBINE = 涡轮
NAME:ALLIEDRADARDISH = 雷达
NAME:ALLIEDREFINERY = 矿石精炼厂
NAME:ALLIEDSALVAGESHIP = 打捞驳船
NAME:ALLIEDSCIENCELAB = 科学设施
NAME:ALLIEDSCOUTINFANTRY = 警犬
NAME:ALLIEDSUPERWEAPON = 超时空传送仪
NAME:ALLIEDSUPERWEAPONADVANCED = 质子撞击炮
NAME:ALLIEDSUPPLYPORT = 补给港务局
NAME:ALLIEDSUPPORTAIRCRAFT = 冰冻直升机
NAME:ALLIEDTECHSCRAMBLER = 科技抑制装置
NAME:ALLIEDTECHSTRUCTURE = 科技中心
NAME:ALLIEDTIMEBOMBLVL1ALLIEDTIMEBOMBLVL1 = 时空炸弹
NAME:ALLIEDTIMEBOMBLVL2ALLIEDTIMEBOMBLVL2 = 高级时空炸弹
NAME:ALLIEDTIMEBOMBLVL3ALLIEDTIMEBOMBLVL3 = 超级时空炸弹
NAME:ALLIEDVIPBUNKER = 盟军 V.I.P.碉堡
NAME:ALLIEDWALLPIECE = 围墙
NAME:ALLIEDWARFACTORY = 装甲工厂
NAME:ALLIEDWARFACTORYREPAIRBAY = 修护厂
NAME:ATTRIBUTECRATE = 属性箱
NAME:BigMamaStatue = 苏联母亲的雕像
NAME:BOMBCRATE = 炸弹箱
NAME:BRIDGEGATEHOUSE = 桥梁警卫室
NAME:BRIDGESECTION = 桥梁
NAME:BUILDALLIEDCRANE = 起重机
NAME:BUILDALLIEDRADARDISH = 雷达
NAME:BUILDSOVIETCRANE = 起重机
NAME:BUILDSOVIETNAVALYARDSALVAGEYARD = 回收压碎厂
NAME:BUILDSOVIETRADARDISH = 雷达
NAME:BUILDSOVIETWARFACTORYSALVAGEYARD = 回收压碎厂
NAME:CIVILIANBUILDINGGARRISONABLE = 平民建筑物
NAME:COMMUNICATORTAB = 通讯器
NAME:CONSTRUCTSOVIETBUNKERSPECIALPOWER = 战斗碉堡
NAME:CRATE = 奖励箱
NAME:DEFENSIVESTRUCTURETECHBUILDING = 发射基地
NAME:EALA = 美商艺电洛杉矶
NAME:EASTERISLANDDEFENSE = 人头像
NAME:EMPERORSONSTATUE = 王子的雕像
NAME:EMPERORSTATUE = 天皇的雕像
NAME:EmperorsTomb = 天皇的陵寝
NAME:EUROPECOASTALGUN = 布莱顿沿岸炮台
NAME:EXPLODINGBARREL = 醒目桶子
NAME:FI_FLOATINGFORTRESSMAINGUN = 波能三门炮
NAME:FLOATINGFORTRESSPOWERCORE = 要塞电缆
NAME:FUTURETECH = 未来科技总部
NAME:FutureTechMiniTower1 = 弹药堆
NAME:FuturetechMinitower2 = 弹道中心
NAME:FuturetechMinitower3 = 引擎室
NAME:FuturetechMinitower4 = 信号阵列
NAME:FUTURETECHSCIENCEBUILDING = 未来科技摩天楼
NAME:GARAGETECHSTRUCTURE = 车库
NAME:GE_SWISSBANK = 瑞士银行
NAME:GIBRALTARHANGAR = 直布罗陀机棚
NAME:GROUNDEDEXPLOSIVEBOMBER = 袋狸轰炸机
NAME:GroundedExplosiveFighter = 天狗战斗机
NAME:HEALINGCRATE = 医疗箱
NAME:HEIDELBERGCASTLE = 苏联总部
NAME:HERMITAGE = 冬宫
NAME:HOSPITALTECHBUILDING = 医院
NAME:IMPERIALADMINBUILDING = 帝国总管理
NAME:IMPERIALHARBORBUILDING = 帝国港口
NAME:JAPANANTIAIRSHIP = 海翼/天翼
NAME:JAPANANTIAIRSHIP_AIR = 天翼
NAME:JAPANANTIAIRSHIP_SEA = 海翼
NAME:JAPANANTIAIRVEHICLE_AIR = 直升机-VX
NAME:JAPANANTIAIRVEHICLE_GROUND = 打击者-VX
NAME:JAPANANTIAIRVEHICLETECH1 = 打击者-VX/直升机-VX
NAME:JAPANANTIINFANTRYINFANTRY = 帝国武士
NAME:JAPANANTIINFANTRYVEHICLE = 机甲天狗/喷气天狗
NAME:JAPANANTIINFANTRYVEHICLE_AIR = 天狗战斗机
NAME:JAPANANTIINFANTRYVEHICLE_GROUND = 天狗机械人
NAME:JAPANANTISTRUCTURESHIP = 将军战舰
NAME:JAPANANTISTRUCTUREVEHICLE = 波能坦克
NAME:JAPANANTIVEHICLEINFANTRY = 坦克杀手
NAME:JAPANANTIVEHICLEINFANTRYTECH3 = 火箭天使
NAME:JAPANANTIVEHICLESHIP = 薙刀巡洋舰
NAME:JAPANANTIVEHICLEVEHICLETECH1 = 海啸坦克
NAME:JAPANANTIVEHICLEVEHICLETECH3 = 鬼王
NAME:JAPANANTIVEHICLEVEHICLETECH1ENERGIZEDARMOR = 纳米偏转装置
NAME:JapanArcherInfantry = 弓箭少女
NAME:JAPANBALLOONBOMBBALLOON = 气球炸弹
NAME:JAPANBARRACKS = 瞬息道场
NAME:JAPANBARRACKSEGG = 道场核心
NAME:JAPANBASEDEFENSE = 防卫者-VX
NAME:JAPANBASEDEFENSEADVANCED = 波能塔
Name:JapanYurikoTech1 = 百合子
Name:JapanYurikoTech2 = 欧米伽百合子
Name:JapanYurikoTech3 = 欧米伽百合子
NAME:JAPANBASEDEFENSEADVANCEDEGG = 塔楼核心
NAME:JAPANBASEDEFENSEEGG = 防卫者核心
NAME:JAPANCOMMANDHQ = 东山高级指挥
NAME:JAPANCOMMANDOTECH1 = 欧米伽百合子
NAME:JAPANCONSTRUCTIONYARD = 建筑工厂
NAME:JAPANCONSTRUCTIONYARDEGG = 建筑工厂
NAME:JAPANECONOMICSTRUCTUREEGG = 经济建筑物
NAME:JAPANEMPEROR = 天皇芳朗
NAME:JAPANEMPERORMECHA = 指挥官贤治
NAME:JAPANENGINEER = 工兵
NAME:JapanFortressShip = 超级要塞
NAME:JapanFortressShip_Air = 超级要塞
NAME:JapanFortressShipEgg = 超级要塞核心
NAME:KenjiVilla = 贤治的总部
NAME:KIROVSTADIUM = 基洛夫发射台
NAME:KR_ARTILLERYDOME = 克里姆林火炮
NAME:KREMLINHEART = 克里姆林的中心
NAME:LAControlTower = 机场控制塔
NAME:LAMediaCenter = 媒体中心
NAME:JAPANINFILTRATIONINFANTRY = 忍者
NAME:JapanIzumi = 野泉
NAME:JAPANKENJIMECHA = 指挥官贤治【红鬼王】
NAME:JAPANLIGHTTRANSPORTVEHICLE = 迅雷运输载具
NAME:JAPANLONGRANGERADAR = 帝国通讯塔
NAME:JAPANMCV = MCV
NAME:JAPANMECHAKING = 将军刽子手
NAME:JAPANMINER = 采矿车
NAME:JAPANNAVALYARD = 帝国码头
NAME:JAPANNAVALYARDEGG = 码头核心
NAME:JAPANNAVALYARDREPAIRBAY = 帝国码头维修站
NAME:JAPANNAVYSCOUTSHIP = 长枪迷你潜艇
NAME:JAPANODESSASPECIALTRANSPORTVEHICLE = 货运载具
NAME:JAPANOREMINERDEPLOYWEAPON = 防护系统
NAME:JAPANOREMINERDEPLOYWEAPONOFF = 货舱
NAME:JAPANPOWERPLANT = 瞬息发电机
NAME:JAPANPOWERPLANTEGG = 发电机核心
NAME:JAPANPOWERPLANTTURBINE = 涡轮机
NAME:JAPANRADARDISH = 雷达
NAME:JAPANRADARSHIP = 帝国雷达舰
NAME:JAPANREFINERY = 矿石精炼厂
NAME:JAPANREFINERYEGG = 矿石精炼厂核心
NAME:JAPANROBOTICSLAB = 天西机械公司
NAME:JapanScientist = 岛田博士
NAME:JAPANSCOUTINFANTRY = 爆裂机械人
NAME:JapanSentinelVehicle = 钢铁浪人
NAME:JAPANSUPERWEAPON = 纳米虫群巢穴
NAME:JAPANSUPERWEAPONADVANCED = 超能波毁灭装置
NAME:JAPANSUPERWEAPONADVANCEDEGG = 毁灭装置核心
NAME:JAPANSUPERWEAPONEGG = 纳米虫群核心
NAME:JAPANTECHSTRUCTURE = 纳米科技电脑主机
NAME:JAPANTECHSTRUCTUREEGG = 电脑主机核心
NAME:JAPANVIPBUNKER = 帝国 V.I.P.碉堡
NAME:JAPANWALLPIECE = 围墙
NAME:JAPANWARFACTORY = 机甲工厂
NAME:JAPANWARFACTORYEGG = 机甲工厂核心
NAME:LASERMTRUSHMORE_JEFFERSON = 杰佛逊胸像
NAME:LASERMTRUSHMORE_JEFFERSON_READY = 末日杰佛逊
NAME:LASERMTRUSHMORE_LINCOLN = 林肯胸像
NAME:LASERMTRUSHMORE_LINCOLN_READY = 末日林肯
NAME:LASERMTRUSHMORE_ROOSEVELT = 罗斯福胸像
NAME:LASERMTRUSHMORE_ROOSEVELT_READY = 末日罗斯福
NAME:LASERMTRUSHMORE_WASHINGTON = 华盛顿胸像
NAME:LASERMTRUSHMORE_WASHINGTON_READY = 末日华盛顿
NAME:LIBERTYSTATUE = 自由女神像
NAME:MONEYCRATE = 现金箱
NAME:MTFUJIVIEWINGTOWER = 天皇的城堡
NAME:NONGARRISONABLESTRUCTURE = 障碍物
NAME:NR_FUTURETECHSCIENCEBUILDING2 = 未来科技研究发展实验室
NAME:NR_FUTURETECHSCIENCEBUILDING3 = 未来科技通讯中心
NAME:NR_FUTURETECHSCIENCEBUILDING4 = 未来科技宅邸
NAME:NR_FutureTechWarFactory = 未来科技兵工厂
NAME:NR_PowerPlnt = 冷却塔
NAME:NR_SigmaHarmonizer = 协调器控制中心
NAME:NY_NYSTOCKEXCHANGE = 纽约证交所
NAME:OBSERVATIONPOSTTECHBUILDING = 监视哨
NAME:ODESSACASTLE = 傲德萨要塞
NAME:ODESSACHURCH = 傲德萨教堂
NAME:ODESSAOPERA = 傲德萨歌剧院
NAME:ORIGINALDOJO = 名椎道馆
NAME:ORIGINALDOCKS = 白田港口
NAME:PLAYERPOWERTELEKINETICPROJECTORDEVICE = 超能波毁灭装置
NAME:PortAuthority = 港口管理处
NAME:PORTSTRUCTURE = 补给港
NAME:PRESIDENTLIMO = 总统的豪华轿车
NAME:RANDOMCRATE = 神秘箱
NAME:RUSHMOREFIRINGBASE = 罗斯摩尔发射基地
NAME:RUSHMOREHEADCONTROLCENTER_JEFFERSON = 杰斐逊头像控制
Name:RushmoreHeadControlCenter_Lincoln = 林肯石像控制
Name:RushmoreHeadControlCenter_Washington = 华盛顿石像控制
NAME:RUSHMORERADARTOWER = 罗斯摩尔通讯塔
NAME:S08SpecialCarrier = 盟军大使
NAME:S08SPECIALDREADNOGHT = 苏联大使
NAME:SA_OBSERVATORYDEFENSIVEGUN = 谷利芬了望台
NAME:SANTAMONICAPIER = 娱乐场机械
NAME:SATELLITELAUNCHFACILITY = K-45 发射台
NAME:ShinzoHouse = 晋三之宅
NAME:SHIPYARDTECHSTRUCTURE = 干船坞
NAME:SHROUDCRATE = 监视箱
NAME:SMOKEBOMBSPECIALPOWER = 烟雾弹
NAME:SOVIETAIRFIELD = 机场
NAME:SOVIETANTIAIRSHIP = 牛蛙载具
NAME:SOVIETANTIGROUNDAIRCRAFT = 双刃直升机
NAME:SOVIETANTIINFANTRYINFANTRY = 征召兵
NAME:SOVIETANTIINFANTRYVEHICLE = 镰刀机甲
NAME:SOVIETANTINAVYSHIPTECH1 = 磁爆快艇
NAME:SOVIETANTINAVYSHIPTECH2 = 阿库拉潜艇
NAME:SOVIETANTISTRUCTURESHIP = 无畏战舰
NAME:SOVIETANTISTRUCTUREVEHICLE = V4 导弹发射车
NAME:SOVIETANTIVEHICLEINFANTRY = 防空部队
NAME:SOVIETANTIVEHICLEVEHICLETECH1 = 铁锤坦克
NAME:SOVIETANTIVEHICLEVEHICLETECH2 = 磁爆坦克
NAME:SOVIETANTIVEHICLEVEHICLETECH3 = 天启坦克
NAME:SOVIETBARRACKS = 军营
NAME:SOVIETBASEDEFENSEADVANCED = 磁爆线圈
NAME:SOVIETBASEDEFENSEAIR = 高射炮
NAME:SOVIETBASEDEFENSEGROUND = 哨兵枪
NAME:SOVIETBOMBERAIRCRAFT = 基洛夫飞船
NAME:SOVIETBUNKER = 战斗碉堡
NAME:SovietChiefEngineer = 首席科学家
NAME:SOVIETCOMMANDOTECH1 = 娜塔莎
NAME:SOVIETCONSTRUCTIONYARD = 建筑工厂
NAME:SOVIETCRANE = 压碎厂起重机
NAME:SovietDesolatorInfantry = 化学部队
NAME:SOVIETENGINEER = 战斗工兵
NAME:SOVIETFIGHTERAIRCRAFT = 米格战斗机
NAME:SovietGrinderVehicle = 粉碎者
NAME:SOVIETHEAVYANTIVEHICLEINFANTRY = 磁爆部队
NAME:SovietHeavyWalkerDeployedTurret = 收割机甲炮塔
NAME:SovietHeavyWalkerVehicle = 收割机甲
NAME:SovietLargeScoutInfantry = 巨熊
NAME:SOVIETMCV = MCV
NAME:SOVIETMINER = 采矿车
NAME:SovietMortarCycle = 火炮机车
NAME:SOVIETNAVALYARD = 海军船坞
NAME:SOVIETNAVALYARDSALVAGEYARD = 回收压碎厂
NAME:SOVIETOUTPOST = 前哨基地
NAME:SOVIETPOWERPLANT = 反应堆
NAME:SOVIETPOWERPLANTADVANCED = 超级反应堆
NAME:SOVIETRADARDISH = 雷达
NAME:SOVIETREFINERY = 矿石精炼厂
NAME:SOVIETSCOUTINFANTRY = 战熊
NAME:SOVIETSCOUTVEHICLE = 恐怖机械人
NAME:SovietStatue = 苏联娱乐场
NAME:SOVIETSUPERWEAPON = 铁幕
NAME:SOVIETSUPERWEAPONADVANCED = 真空内爆弹
NAME:SOVIETSURVEYOR = 史普尼克勘查车
NAME:SOVIETTECHSTRUCTURE = 战斗研究所
NAME:SOVIETVIPBUNKER = 苏军 VIP 碉堡
NAME:SOVIETWALLPIECE = 围墙
NAME:SOVIETWARFACTORY = 战争工厂
NAME:SOVIETWARFACTORYSALVAGEYARD = 回收压碎厂
NAME:ST_LENINGRADMISSLEBASE = 障碍物
NAME:ST_LENINGRADMISSLEBASE_01 = 国家火炮博物馆
NAME:ST_SHUTTLEBUILDING = 列宁格勒要塞
NAME:SUPERWEAPONTIMERCHRONOSPHERE = 超时空传送仪
NAME:SUPERWEAPONTIMERIRONCURTAIN = 铁幕
NAME:SUPERWEAPONTIMERNANOSWARM = 纳米虫群巢穴
NAME:SUPERWEAPONTIMERPARTICLECANNON = 质子撞击炮
NAME:SUPERWEAPONTIMERTELEKINETIC = 超能波毁灭装置
NAME:SUPERWEAPONTIMERVACUUMBOMB = 真空内爆弹
NAME:TECHBUILDINGOILDERRICK = 钻井高塔
NAME:TECHBUILDINGORENODE = 矿脉
NAME:TECHBUILDINGORENODE2 = 双矿脉
NAME:TECHBUILDINGORENODE4 = 四矿脉
NAME:TECHBUILDINGPOWERPLANT = 工业发电厂
NAME:TH_JapanHiveGenerator = 纳米虫群 EX
NAME:TOGGLEARMORUPOFF = 货舱
NAME:UNITCRATE = 部队箱
NAME:VETERANCYCRATE = 经验箱
NAME:VETERANCYTECHSTRUCTURE = 精兵学院
NAME:VOLCANOFORTRESS = 火山要塞
NAME:WEAPONSCRAMBLESPECIALPOWER = 武器干扰装置
起义时刻 CSF 技能名称
NAME:ABILITYALLIEDBASEDEFENSEEVACUATE = 撤离占有者
NAME:ABILITYCIVILIANSTRUCTUREEVACUATE = 净空建筑物
NAME:ABILITYDISGUISEDEVACUATE = 撤离乘员
NAME:ABILITYEVACUATEALL = 撤离乘员
NAME:ABILITYJAPANANTIINFANTRYINFANTRYBONZAI = 万岁冲锋
NAME:ABILITYJAPANENGINEERSPRINT = 急奔
NAME:ABILITYJAPANSCOUTINFANTRYBOMB = 自爆
NAME:ABILITYPACKUPALLIEDMCV = 打包
NAME:ABILITYPACKUPJAPANMCV = 打包
NAME:ABILITYPACKUPSOVIETMCV = 打包
NAME:ABILITYPARADROP = 空投
NAME:ABILITYSOVIETANTIGROUNDAIRCRAFTEVACUATE = 撤离乘员
NAME:ABILITYSOVIETBATTLEBUNKEREVACUATEALL = 撤离碉堡
NAME:ACTIVATEMAGNETICARMOR = 黑洞装甲
NAME:ACTIVATEMAGNETICARMOROFF = 主炮
NAME:ACTIVATEMIRAGEFIELDOFF = 攻击模式
NAME:ACTIVATESHORTCIRCUIT = 电磁干扰器
NAME:ACTIVATESHORTCIRCUITOFF = 磁爆线圈枪
NAME:ACTIVATESHORTCIRCUITOFFTANK = 双磁爆线圈
NAME:ACTIVATESHORTCIRCUITTANK = 电磁干扰器
NAME:ACTIVATESUPERSONICABILITY = 后燃器
NAME:ACTIVATETARGETPAINTER = 目标标定器
NAME:ACTIVATETARGETPAINTEROFF = 主炮
NAME:AGGRESIVESTANCE = 侵略姿态
NAME:AGGRESSIVESTANCE = 侵略姿态
NAME:AIASSAULTDIRECTIVE = 计划攻击
NAME:AIHOLDOBJECTDIRECTIVE = 攻击目标
NAME:AIHOLDPOSITIONDIRECTIVE = 占领据点
NAME:AINORMALDIRECTIVE = 继续指挥
NAME:AIRCRAFTQUEUECONSOLE = 空中部队
NAME:ALLIEDAIRFIELDRETURNTOBASE = 唤回飞行器
NAME:ALLIEDANTIGROUNDAIRCRAFTRETURNTOAIRFIELD = 返回基地
NAME:ALLIEDANTIINFANTRYVEHICLEABILITY = 撤离乘员
NAME:ALLIEDENGINEERHEALTOGGLE = 急救帐棚
NAME:ALLIEDENGINEERHEALTOGGLEOFF = 打包
NAME:ALLIEDFIGHTERAIRCRAFTRETURNTOAIRFIELD = 返回基地
NAME:AlliedFutureTankLaserWeapon = 暴乱光束
NAME:ArcherArrowBarrageSpecialPower = 弹幕射击
NAME:ASSAULTMOVE = 攻击移动
NAME:ATTACKMOVE = 行进攻击
NAME:BARKSPECIALPOWER = 增幅咆哮
NAME:BASEDEFENSETRANSFORMSPECIALPOWER = 空防模式
NAME:BASEDEFENSETRANSFORMSPECIALPOWEROFF = 防卫者模式
NAME:BRIBESPECIALPOWER = 贿赂
NAME:BUTTONJAIV_TRANSFORM = 喷气模式
NAME:BUTTONJAIV_TRANSFORMOFF = 机甲模式
NAME:CONTEXTUALTAB = 关联标签
NAME:CONTROLGROUPSTAB = 控制群组
NAME:ConventionCenter = 会议中心
NAME:COOPAIASSAULTBUTTON = 计划攻击
NAME:COOPAIHOLDOBJECTBUTTON = 攻击目标
NAME:COOPAIHOLDPOSITIONBUTTON = 占领据点
NAME:COOPAINORMALBUTTON = 继续指挥
NAME:CRYOLEAPSPECIALPOWER = 跳跃撞击
NAME:DEACTIVATEMISSIONHOTSPOTSBUTTON = 取消副指挥官出击
NAME:DesolatorWeaponMode = 溅射模式
NAME:DesolatorWeaponModeOff = 死亡喷雾模式
NAME:EJECTPASSENGERSSPECIALPOWER = 弹射乘员
NAME:EMPCRUISEMISSLESPECIALPOWER = 断电导弹
NAME:FASTFORWARD = 快转
NAME:FORCEATTACK = 强制攻击
NAME:FORCEMOVE = 压碎移动
NAME:GUARDSTANCE = 警戒姿态
NAME:HARPOONSPECIALPOWER = M-鱼叉导弹
NAME:HARPOONSPECIALPOWEROFF = 主炮
NAME:HOLDFIRESTANCE = 停火姿态
NAME:HOLDGROUNDSTANCE = 固守姿态
NAME:INFILTRATED = 被渗透的%s
NAME:JAPANANTIAIRSHIPTRANSFORM = 腾空
NAME:JAPANANTIAIRSHIPTRANSFORMOFF = 潜海
NAME:JAPANANTIAIRVEHICLETECH1TRANSFORM = 直升机模式
NAME:JAPANANTIAIRVEHICLETECH1TRANSFORMOFF = 打击者模式
NAME:JAPANANTISTRUCTURESHIPRAMMINGSPEED = 冲撞速度
NAME:JAPANANTISTRUCTUREVEHICLEFIREKICANNON = 提早发射
NAME:JAPANANTIVEHICLEVEHICLETECH3RUSHATTACK = 狂牛快攻
NAME:JAPANBASEDEFENSEADVANCED_FIREKICANNON = 提早发射
NAME:JapanFortressShipEggUnpackSpecialPower = 展开
NAME:JapanFortressShipTransformAircraftMode = 空中要塞模式
NAME:JapanFortressShipTransformShipMode = 海上要塞模式
NAME:JUMPSPECIALPOWER = 高飞跳跃
NAME:KAMIKAZEATTACKSPECIALPOWER = 最后航程
NAME:KAMIKAZEATTACKSPECIALPOWEROFF = 猎杀模式
NAME:LaserGlaiveBlastSpecialPower = 能量波
NAME:LeapDeploySpecialPower = 原型跳跃
NAME:LEAPSPECIALPOWER = 跳蚤跳跃
NAME:MAGNETICBOMBSPECIALPOWER = 磁雷
NAME:MAGNETICBOMBSPECIALPOWEROFF = 高射炮
NAME:MAGNETICSATELLITEEFFECTLVL1 = 牵引光束
NAME:MAGNETICSATELLITEEFFECTLVL2 = 超级牵引光束
NAME:MAGNETICSATELLITEEFFECTLVL3 = 究极牵引光束
NAME:MECHAKINGSHOCKWAVESPECIALPOWER = 欧米伽震波
NAME:MEERAGETANK = 低调的苏联坦克
NAME:MIRVSPECIALPOWER = 多重弹头
NAME:MIRVSPECIALPOWEROFF = 精准弹头
NAME:MOLOTOVCOCKTAILSPECIALPOWER = 汽油弹
NAME:MOLOTOVCOCKTAILSPECIALPOWEROFF = 突击步枪
NAME:NitrousBoostSpecialPower = 涡轮增压
NAME:OpenPlayerYurikoTechStore = 超能波天赋
NAME:OPENSTANCES = 改变姿态
NAME:PILOTSNIPESPECIALPOWER = 狙击驾驶
NAME:POWERMODE = 电力模式
NAME:POWERSTAB = 辅助能力
NAME:PSYONICBLASTSPECIALPOWER = 超能波爆破
NAME:RADARLOCKSPECIALPOWER = 激光导向模式
NAME:RADARLOCKSPECIALPOWEROFF = 自行导向模式
NAME:RAPIDLAUNCHSPECIALPOWER = 牺牲发射器
NAME:RAPIDLAUNCHSPECIALPOWEROFF = 安全模式
NAME:RedAlertButton = 红色警戒
NAME:REPAIRMODE = 修复模式
NAME:REPAIRMODECONSOLE = 修复模式
NAME:REVERSEMOVE = 倒退移动
NAME:ROARSPECIALPOWER = 增幅怒吼
NAME:SELLMODE = 出售模式
NAME:SELLMODECONSOLE = 出售模式
NAME:SOVIETAIRFIELDRETURNTOBASE = 唤回飞行器
NAME:SOVIETFIGHTERAIRCRAFTRETURNTOAIRFIELD = 返回基地
NAME:SPECIALPOWERSHRINKRAY = 微缩光束
NAME:SUPERTORPEDOSSPECIALPOWER = 超级鱼雷
NAME:TESLANOVASPECIALPOWER = 磁爆突波
NAME:TESLASINGULARITY = 独特的磁暴
NAME:THREATMETER = 威胁指示器
NAME:TIMEBELTSPECIALPOWER = 时空腰带
NAME:TOGGLEAFTERBURNERS = 超燃器
NAME:TOGGLEAFTERBURNERSOFF = 推进器
name:togglealliedartilleryautocannon = 收起火炮
name:togglealliedartillerysiegeweapon = 布署火炮
name:togglealliedgunship = 链炮
name:togglealliedgunshipautocannon = 撞击炮
NAME:TOGGLEARMORUP = 反应装甲
NAME:TOGGLEBINARYWEAPON = 电力静止射线
NAME:TOGGLEBINARYWEAPONOFF = 撕裂钢爪
NAME:TOGGLELEECHBEAM = 汲取光束
NAME:TOGGLELEECHBEAMOFF = 主要武器
NAME:TOGGLELOCKDOWNGUNSPECIALPOWER = 瘫痪鞭
NAME:TOGGLELOCKDOWNGUNSPECIALPOWEROFF = 战斗模式
NAME:TOGGLERIOTSHIELDUPGRADE = 镇暴盾牌
NAME:TOGGLERIOTSHIELDUPGRADEOFF = 霰弹枪
NAME:TOGGLESHIELDSPHERE = 能量护盾
NAME:ToggleSovietMortarcycleMolotov = 汽油弹满天飞
NAME:ToggleSovietMortarcycleMortar = 机动火炮
NAME:TOGGLESPIDERHOLE = 蜘蛛洞穴
NAME:TOGGLESPIDERHOLEOFF = 离开洞穴
NAME:TORPEDOSPREADSPECIALPOWER = S 型鱼雷
NAME:UPGRADEALLIEDTECH2 = 高级许可
NAME:UPGRADEALLIEDTECH3 = 最高许可
NAME:UPGRADEJAPANBARRACKSTECH2 = 纳米科技升级
NAME:UPGRADEJAPANBARRACKSTECH3 = 道场突破
NAME:UPGRADEJAPANNAVALYARDTECH2 = 码头升级
NAME:UPGRADEJAPANNAVALYARDTECH3 = 码头突破
NAME:UPGRADEJAPANWARFACTORYTECH2 = 纳米科技升级
NAME:UPGRADEJAPANWARFACTORYTECH3 = 机甲工厂突破
NAME:VARIABLEWEAPONTRANSFORMOFF2 = 地面切割模式
NAME:WEAPONSCRAMBLESPECIALPOWEROFF = 防空炮
NAME:YURIKO_POWERS_MENU = 超能波天赋
起义时刻 CSF 支援(机密)技能
NAME:CAMPAIGNPLAYERPOWERPARADROPLVL1 = 伞兵队
NAME:CAMPAIGNPLAYERPOWERPARADROPLVL2 = 伞兵班
NAME:CAMPAIGNPLAYERPOWERPARADROPLVL3 = 伞兵排
NAME:PLAYERCONTROLGROUPS = 控制群组
NAME:PLAYERPOWERAIRPOWER = 先进航空学
NAME:PLAYERPOWERALLIEDFREETRADE = 自由贸易
NAME:PLAYERPOWERCHRONORIFTLVL1 = 超时空裂隙
NAME:PLAYERPOWERCHRONORIFTLVL2 = 超时空裂口
NAME:PLAYERPOWERCHRONORIFTLVL3 = 超时空裂缝
NAME:PLAYERPOWERCHRONOSPHERE = 超时空传送仪
NAME:PLAYERPOWERCHRONOSWAP = 超时空变换
NAME:PLAYERPOWERCRUSHPUPPIES = 重机蹂躏
NAME:PLAYERPOWERCRYOSATELLITELVL1 = 冰冻射击
NAME:PLAYERPOWERCRYOSATELLITELVL2 = 冰冻轰击
NAME:PLAYERPOWERCRYOSATELLITELVL3 = 冰冻暴击
NAME:PLAYERPOWERDESOLATORBOMB_LEVEL1 = 毁灭空袭
NAME:PLAYERPOWERDESOLATORBOMB_LEVEL2 = 毁灭双重空袭
NAME:PLAYERPOWERDESOLATORBOMB_LEVEL3 = 毁灭三角空袭
NAME:PLAYERPOWERFINALSQUADRON_L1 = 决胜中队
NAME:PLAYERPOWERFINALSQUADRON_L2 = 决胜中队 X
NAME:PLAYERPOWERFINALSQUADRON_L3 = 决胜中队欧米伽
NAME:PLAYERPOWERHIGHTECHNOLOGY = 高科技
NAME:PLAYERPOWERIRONCURTAIN = 铁幕
NAME:PLAYERPOWERIRRADIATETARGET = 毒质腐蚀
NAME:PLAYERPOWERJAPANADVANCEDMISSILEPACKS = 先进火箭匣
NAME:PLAYERPOWERJAPANAMBUSH = 惊骇伏击
NAME:PLAYERPOWERJAPANBALLOONATTACK_L1 = 气球炸弹
NAME:PLAYERPOWERJAPANBALLOONATTACK_L2 = 气球炸弹爆炸
NAME:PLAYERPOWERJAPANBALLOONATTACK_L3 = 气球炸弹火力攻击
NAME:PLAYERPOWERJAPANEMPERORSRESOLVE_L1 = 天皇之怒
NAME:PLAYERPOWERJAPANEMPERORSRESOLVE_L2 = 天皇复仇
NAME:PLAYERPOWERJAPANEMPERORSRESOLVE_L3 = 天皇惩罚
NAME:PLAYERPOWERJAPANENHANCEDKAMIKAZE = 光荣自爆
NAME:PLAYERPOWERJAPANNAVALPOWER = 强化舰队
NAME:PLAYERPOWERJAPANROBOTICASSEMBLY = 机械化组装
NAME:PLAYERPOWERMAGNETICSATELLITELVL1 = 磁力卫星
NAME:PLAYERPOWERMAGNETICSATELLITELVL2 = 超级磁力卫星
NAME:PLAYERPOWERMAGNETICSATELLITELVL3 = 超磁力卫星
NAME:PLAYERPOWERMAGNETICSINGULARITY = 超凡磁力
NAME:PLAYERPOWERNANOSWARMHIVE = 纳米虫群
NAME:PLAYERPOWERORBITALREFUSE_RANK1 = 轨道坠落
NAME:PLAYERPOWERORBITALREFUSE_RANK2 = 轨道抛掷
NAME:PLAYERPOWERORBITALREFUSE_RANK3 = 轨道垃圾雨
NAME:PLAYERPOWERPARTICLECANNON = 质子撞击炮
NAME:PLAYERPOWERPOINTDEFENSEDRONES = 单点防御无人载具
NAME:PLAYERPOWERPRECISIONSTRIKE = 精准攻击
NAME:PLAYERPOWERPRODUCTIONKICKBACKS = 现金奖励
NAME:PLAYERPOWERSATELLITE = 侦察扫瞄
NAME:PLAYERPOWERSOVIETMASSPRODUCTION = 大量生产
NAME:PLAYERPOWERTERRORDRONEEGGS = 恐怖机械人袭击
NAME:PLAYERPOWERTIMEBOMBLVL1 = 时空炸弹
NAME:PLAYERPOWERTIMEBOMBLVL2 = 高级时空炸弹
NAME:PLAYERPOWERTIMEBOMBLVL3 = 超级时空炸弹
NAME:PLAYERPOWERVACUUMBOMB = 真空内爆弹
NAME:PlayerPowerYurikoLureRank1 = 超能波支配
NAME:PlayerPowerYurikoLureRank2 = 超能波支配 II
NAME:PlayerPowerYurikoLureRank3 = 超能波支配 III
NAME:PlayerPowerYurikoShieldRank1 = 超能波护盾
NAME:PlayerPowerYurikoShieldRank2 = 超能波护盾 II
NAME:PlayerPowerYurikoShieldRank3 = 超能波护盾 III
NAME:PlayerPowerYurikoSlamRank1 = 心灵抛击
NAME:PlayerPowerYurikoSlamRank2 = 心灵抛击 II
NAME:PlayerPowerYurikoSlamRank3 = 心灵抛击 III
NAME:PlayerPowerYurikoUpgradeAttackDamage01 = 蔑视
NAME:PlayerPowerYurikoUpgradeAttackDamage02 = 蔑视 II
NAME:PlayerPowerYurikoUpgradeHealth01 = 冷感
NAME:PlayerPowerYurikoUpgradeHealth02 = 冷感 II
NAME:PlayerPowerYurikoUpgradeSpeed01 = 急躁
NAME:PlayerPowerYurikoUpgradeSpeed02 = 急躁 II
W3X 模型初解
属于迟到的教程吧，研究起步兵的应该了解这些。首先用写字板将 w3x 打开……
<W3DHierarchy/>骨架，有时在 SKN 里，但是，如果骨骼动画复杂的话，一般都提取
为 SKL
<W3DMesh id="JUSKYWOLF_SKN.juantiinfantryvehicle"
GeometryType="Skin">这个是在_SKN 里的模型
<BoundingBox/> 边界盒，没有它就无法选取
<BoundingSphere Radius="18.241304"/>边界球体，这个球应该是程序自己算的，
max 里没有这个值
<Vertices/>顶点，应该是模型的构成
<Normals/>标准
<Tangents/>切线
<Binormals/>法线，确定模型的正面是向外，还是向内
<TexCoords/>可塑坐标
<BoneInfluences/>骨骼影响，如果 GeometryType="Skin"则有此字段，
GeometryType="Normals"则没有这个字段，这个很重要，应该是模型和骨骼的衔接，蒙
皮必须采用 WWSkin，其他各类蒙皮无效。
<ShadeIndices/>Shade 参数，里面包括所用的 FX 插件，还有贴图
<Triangles/>三角函数
<FXShader/>想要调用的 FX，这个应该是 RA3 里固定的那几个
<W3DCollisionBox/>碰撞
<W3DContainer/>容器，这里包括可能调用的 SKL，还有边界盒
<SubObject/>子物体
<W3DAnimation/>动画，一般会单独提取出来，但极个别的会在 SKN 里
<Channels>通道，每个通道代表一节骨骼，里面则是各帧动画
OCL 产生新物体的重要参数
DispositionType 位置，角度，动画，具体值如下
1.
2. DISPOSITION_NONE 没有部署，没有计划
3. LIKE_EXISTING 现有的
4. ON_GROUND_ALIGNED 地面上的排列
5. SEND_IT_FLYING 让他飞起
6. SEND_IT_UP 让他起来
7. SEND_IT_OUT 让他出来
8. RANDOM_FORCE 随机的力量
9. FLOATING 浮动
10. INHERIT_VELOCITY 继承速度
11. FORWARD_IMPACT 向前影响力
12. REVERSE_IMPACT 相反影响力
13. BUILDING_CHUNKS 建筑块
14. ANIMATED 动画
15. ABSOLUTE_ANGLE 绝对角度
16. SPAWN_AROUND 产卵在周围
17. RELATIVE_ANGLE 相对角度
18. USE_WATER_SURFACE 在水面使用
19. USE_CLIFF 在悬崖使用
20. CLAMP_TO_GROUND 夹在地面上
21. FALL_TO_GROUND 落到地面上
22. USE_DYNAMICS_FOR_FLING 使用动力学起飞
复制代码
Option 选项

【代码篇】红警 3DIY---进阶篇
翻译：游侠 woshifyf
高手请指正纰漏。
进阶篇主要包括包括：
1. 如何修改单位图标
2. 修改单位的更多信息
3. 改变单位和建筑的建造时间和花费
4. 改变一个用户或是建筑的科技附属性
5. 改变单位或者建筑的武器
6. 关于武器修改的更多消息
7. 为单位或者建筑添加维修蜂
8. 如何编辑单位经验等级
9. 如何改变特殊能力模板
10. （附加）机密协议相关代码 XML 解释
--------------------------------------------------------------------------------------------------
如何修改单位图标
嗨，这次是关于 cameo 的教程，Cameos,或许你不知道，正是用来作为单位图标的图像，
正是因为使用了它们，你在训练一个单位，或是建造一个建筑时，你知道你在训练什么，在
建造什么，所以对于新的单位或是修改已有的单位来说，这是很重要的。今天，我们将学习
去编辑一个新单位的 cameo，我们还用 mytank 的例子。
这里是他的主要设置：
<GameObject
id=”mytank”
inheritFrom=”BaseVehicle”
SelectPortrait=”Portrait_AlliedAntiVehicleVehicleTech1″ !
ButtonImage=”Button_AlliedAntiVehicleVehicleTech1_on” !
Side=”Allies”
SubGroupPriority=”425″
EditorSorting=”UNIT”
HealthBoxHeightOffset=”25″
BuildTime=”10″
CommandSet=”mytankCommandSet”
KindOf=”SELECTABLE CAN_ATTACK CAN_CAST_REFLECTIONS SCORE VEHICLE
CAN_BE_FAVORITE_UNIT T2_UNIT”
WeaponCategory=”CANNON”
VoicePriority=”188″
EditorName=”mytank”
Description=”Desc:mytank”
TypeDescription=”Type:mytank”
UnitIntro=”Allied_GuardianTank_UnitIntro”>
<DisplayName
xai:joinAction=”Replace”
xmlns:xai=”uri:ea.com:eala:asset:instance”>Name:mytank</DisplayName>
有两个地方是和改变 cameo 有关的：
SelectPortrait=”Portrait_AlliedAntiVehicleVehicleTech1″
ButtonImage=”Button_AlliedAntiVehicleVehicleTech1_on”
现在，我们把上面文本括号里面的内容变为“Portrait_mytank”，当然，脚本会要求一个按钮
图像和肖像，当然这两个可以不一样，但为了简单起见，我们使用一样的图像。
现在，保存并关闭它，我们进入图像文件夹 RA3 MOD SDK\Art\images
如 果 你 看 到 了 先 驱 者 炮 艇 的 肖 像 ， 那 你 就 来 对 了 。 现 在 ， 我 们 要 复 制
SampleUpdatedPackedImages.xml 文件，把它重命名为 SampleUpdatedPackedImages 2，
现在，打开它，删除下面内容出现之前所有内容:
<?xml version=’1.0′ encoding=’UTF-8′?>
<AssetDeclaration xmlns=”uri:ea.com:eala:asset”
xmlns:xsi=”http://www.w3.org/2001/XMLSchema-instance”>
<Texture id=”Portrait_AlliedHarbingerGunship” File=”Portrait_AlliedHarbingerGunship.tga”
OutputFormat=”A8R8G8B8″ GenerateMipMaps=”false” AllowAutomaticResize=”false”/>
< ackedTextureImage id=”Portrait_AlliedHarbingerGunship”
Texture=”Portrait_AlliedHarbingerGunship” Rotated=”false”>
<Dimensions x=”128″ y=”128″/>
<Coords x=”0″ y=”0″/>
<TextureDimensions x=”128″ y=”128″/>
</PackedTextureImage>
</AssetDeclaration>
好 的 ， 现 在 我 们 要 做 的 就 是 把 每 个 “Portrait_AlliedHarbringerGunship” 置 换 为
“Portrait_mytank”。
一旦完成了上述的操作，保存并关闭.xml 文件。现在，我们所需要做的就是制作肖像。使
用 你 最喜 欢 的 画 图 程序（ 要 能 够 编辑 TGA 格式 ） ，最 重要 的是 要把画 的 图 命 名 为
Portrait_mytank，并且你要把它存在 image 文件夹下，跟先驱者的肖像放在一起。
注意：图像尺寸最好在 128*128 或 76*106，如果不是，会自动调整大小，但我不喜欢这样。
现在让我来解释我们刚才做的，新的 cameo 必须通 SampleUpdatedPackedImages 这种文
件来引入 mod 中，否则，他们不会被使用。
OK，该最后一步了，前往 mod.xml 文件，在最下方，/asset declaration 标签之上，加入如
下内容：
<!– New sample portrait –>
<Include type=”all” source=”ART:Images/SampleUpdatedPackedImages2.xml” />
现在，build 阁下的 mod 并享受吧，如果没效果，那么检查你的文件名，确保他们相同。
------------------------------------------------------------------------------------------------
修改单位的更多信息
关于单位的文件可以在 SageXml\阵营名称\Units 文件夹下找到（Allied：盟军 japan：日本
Soviet:苏联）
让我们来看如何修改磁暴步兵。
找到 Soviet/Units/SovietHeavyAntiVehicleInfantry.xml.
好吧..我知道..EA 使用的名字转换并不是很直白，但你要适应。（单位的 xml 文件的名字不
是其真实的名字，而是另一种名字，比如磁暴步兵，就是在这里的名字就是苏联重型反载具
步兵，大家可以根据它们这里名字的意思来推测它们是哪种单位，heavy 是重型，Anti 的意
思是反，克，venhicle 是载具，infantyr 是步兵，Air 是空军，navyship 是海军，structure
是建筑，bomber 是炸弹。Fighter 是战斗机，。。解释这些可能多余了）
然后打开单位的文件。
我们看到了一长串的<Include type="all"。。。词条，好的，这些都是用来告诉游戏要使用
那些单位动画（动作）。现在还不是那么有趣。
<Include type=”instance” source=”DATA:BaseObjects/BaseInfantry.xml” />意味着这个单
位将使用在 BaseInfantry.xml 文件中定义的一般类步兵单位使用的基本动作。所有的步兵单
位都链接到这个基础的文件上。
下面是关键的部分了：
‘inheritFrom=’与上面的并不是十分相同，区别在于，上一个是用于视觉（art），而另一个
是用于单位的实际的基本特性.
‘id=’只是每个单位或是物件所需要的独特的标识符。可以随便设，但如果你要引用这个单位
的话，要记住它。
‘SelectPortrait’ 和 ‘ButtonImage’对应着两个图标，一个是你在游戏中选择它时的图像，另
一个则是建造界面上的图像。
‘Side=”Soviet”这个很明显，磁暴步兵是苏联的单位 （side：阵营）
‘BuildTime=’很重要，决定了单位的制造时间，以秒为单位。
‘CommandSet=’是一个特定的单位的特定的动作集，在这里不讨论。
‘KindOf=’一个制约环境来过滤这个单位可以做什么，不可以做什么
‘SELECTABLE’ 意味着你可以选中这个单位。‘CAN_ATTACK’意味着这个单位可以攻击目标
‘INFANTRY’意味着这个单位是步兵单位，当然，也可以是别的。
‘VoicePriority’（语音优先级）被用在当你选择了一群不同类型的单位的情况。优先级高的单
位会语音响应你的选中。比如，如果你同时选中了动员兵和磁暴步兵，磁暴步兵的语音将被
播放。
‘Description’ 和 ‘TypeDescription’这两个标签定义了你在单位的制造界面上可以看到的描
述说明。文本信息可以通过字段文件（mod.str）来自定义。
‘HealthBoxHeightOffset’标示单位的生命条在哪里显示，用默认的就行了。
‘UnitIntro’ 在你建造一个单位时，所播放的声音。
‘GameDependency’定义制造该单位需要什么前提。
<GameDependency
id=”ModuleTag_GameDependency”>
<RequiredObject>SovietPowerPlantAdvanced</RequiredObject>
</GameDependency>
从上面我们可以看到，磁暴步兵需要 SovietPowerPlantAdvanced 苏联的核电厂，实际的
生产建筑没有列出来（苏联兵营），列出来是多此一举。
‘BuildCost’标签中的‘Amount=’的值表示该单位的造价。
<BuildCost Account=”=$ACCOUNT_ORE” Amount=”750″/>可以看到，磁暴步兵的造价是
750。你可以任意修改这个值，不会影响别的东西，我建议你保持一个成比例的性价比。
‘ArmorSet’子段里的‘Armor=’定义了这个单位是何种装甲类型。这很重要，如果你想改变武
器对不同护甲的伤害。
告诉我们这个单位怎样移动，我建议最好不要乱改。最好在你确定要做的情况下改变。你所
能做的是修改‘Speed=’值，代表单位的速度。
然后是一大堆我们不愿理的动作条。
还有两个你是愿意修改的。
一个是单位的生命
一个单位的生命在‘Body’子段中如下定义：
<Body>
<ActiveBody
id=”ModuleTag_Body”
MaxHealth=”250″ />
</Body
‘MaxHealth=’可以改为随便一个正整数，我没试过改负数，也不推荐这样做。
第 2 个就是单位的武器。武器定义在‘WeaponSetUpdate’上，
让我们来看一看磁暴步兵的武器：
Let’s see the Tesla Trooper’s weapon:
<WeaponSetUpdate
id=”ModuleTag_WeaponSetUpdate”>
<WeaponSlotHardpoint
ID=”1″>
<Weapon
Ordering=”PRIMARY_WEAPON”
Template=”SovietHeavyAntiVehicleInfantryTeslaGun”
ForbiddenObjectStatus=”GENERIC_TOGGLE_STATE CHARGING_BASE_DEFENSES”/>
<Weapon
Ordering=”SECONDARY_WEAPON”
Template=”SovietHeavyAntiVehicleInfantryTeslaLinkGun”
ForbiddenObjectStatus=”GENERIC_TOGGLE_STATE”/>
</WeaponSlotHardpoint>
</WeaponSetUpdate>
有两个武器，定义为 primary 主武器和 secondary 副武器
不幸的是你不能在这里编辑它们，因为武器专门在 Weapon.xml 文件中定义。
如 果 你 要 修 改 它 们 ， 你 要 打 开 Weapon.xml 文 件 ， 搜 索
‘SovietHeavyAntiVehicleInfantryTeslaGun’ 和‘SovietHeavyAntiVehicleInfantryTeslaLinkGun’
武器将在另一章讨论，本章结束
-----------------------------------------------------------------------------------------------------------
怎样改变单位和建筑的建造时间和花费
还用我们在以第一个教程中的坦克例子，你可以发现修改建造时间和花费简直是小菜一碟。
只要修改下划线部分就可以了。
<GameObject
id=”mytank”
inheritFrom=”BaseVehicle”
SelectPortrait=”Portrait_AlliedAntiVehicleVehicleTech1″
ButtonImage=”Button_AlliedAntiVehicleVehicleTech1_on”
Side=”Allies”
SubGroupPriority=”425″
EditorSorting=”UNIT”
HealthBoxHeightOffset=”25″
BuildTime=”10″建造时间=10 秒
CommandSet=”mytankCommandSet”
KindOf=”SELECTABLE CAN_ATTACK CAN_CAST_REFLECTIONS SCORE VEHICLE
CAN_BE_FAVORITE_UNIT T2_UNIT”
WeaponCategory=”CANNON”
VoicePriority=”188″
EditorName=”mytank”
Description=”Desc:mytank”
TypeDescription=”Type:mytank”
UnitIntro=”Allied_GuardianTank_UnitIntro”>
<DisplayName
xai:joinAction=”Replace”
xmlns:xai=”uri:ea.com:eala:asset:instance”>Name:mytank</DisplayName>
<ObjectResourceInfo>
<BuildCost Account=”=$ACCOUNT_ORE” Amount=”950″ /花费 =950>
</ObjectResourceInfo>
How to change the dependancy of a unit or structure 怎样改变一个用户或是建筑的科技附
属性
一个单位的附属性就是建造这个单位所需要建造的建筑或是要进行的研究。使用前面的坦克
例子来看看。
<GameObject
id=”mytank”
inheritFrom=”BaseVehicle”
SelectPortrait=”Portrait_AlliedAntiVehicleVehicleTech1″
ButtonImage=”Button_AlliedAntiVehicleVehicleTech1_on”
Side=”Allies”
SubGroupPriority=”425″
EditorSorting=”UNIT”
HealthBoxHeightOffset=”25″
BuildTime=”10″
CommandSet=”mytankCommandSet”
KindOf=”SELECTABLE CAN_ATTACK CAN_CAST_REFLECTIONS SCORE VEHICLE
CAN_BE_FAVORITE_UNIT T2_UNIT”
WeaponCategory=”CANNON”
VoicePriority=”188″
EditorName=”mytank”
Description=”Desc:mytank”
TypeDescription=”Type:mytank”
UnitIntro=”Allied_GuardianTank_UnitIntro”>
<DisplayName
xai:joinAction=”Replace”
xmlns:xai=”uri:ea.com:eala:asset:instance”>Name:mytank</DisplayName>
<ObjectResourceInfo>
<BuildCost Account=”=$ACCOUNT_ORE” Amount=”950″/>
</ObjectResourceInfo>
<GameDependency>
<NeededUpgrade>Upgrade_AlliedTech2</NeededUpgrade>
</GameDependency>
下划线部分表示我们的坦克需要盟军的高级授权来建造。删除它，就可以使得该单位的建造
不再有附属性。
当然，你也可以根据你所设的附属性等级来修改粗体部分，你可以选择 1，2，3。（这一行
的作用是设定单位的某些属性，单位属于几级单位）
---------------------------------------------------------
怎样改变单位或是建筑的武器
还使用以前的坦克作例子，把其 xml 文件拉到下面所示文本处，当然，你也可以使用搜索功
能来搜索“weapon”
<WeaponSetUpdate
id=”ModuleTag_WeaponSetUpdate”>
<WeaponSlotTurret
ID=”1″>
<Weapon
Ordering=”PRIMARY_WEAPON”
Template=”AlliedAntiVehicleVehicleTech1Cannon”
ForbiddenObjectStatus=”GENERIC_TOGGLE_STATE”/>
<Weapon
Ordering=”SECONDARY_WEAPON”
Template=”AlliedAntiVehicleVehicleTech1TargetPainter”
ObjectStatus=”GENERIC_TOGGLE_STATE”/>
<TurretSettings
TurretTurnRate=”360″
MinimumPitch=”-30d”
AllowsPitch=”true”
TurretPitchRate=”180″
MinIdleScanTime=”1.0s”
MaxIdleScanTime=”4.0s”
MinIdleScanAngle=”30.0″
MaxIdleScanAngle=”50.0″
ComeToHaltJiggle=”3d”>
<TurretAITargetChooserData
IdleScanDelay=”=$FAST_IDLE_SCAN_DELAY”
CanAcquireDynamicIfAssignedOutOfRange=”true” />
</TurretSettings>
</WeaponSlotTurret>
从上面可以看到，这个单位有两种武器，因为是取自守护者坦克，因此有一个探测瞄准器作
为副武器，现在我们只需关注主武器（下划线部分）。可以把它替换为其他的武器模板，只
要查看别的单位的武器模板的名称就可以了，或者直接看 weapon.xml 文件。要记住，有些
武器比如激光类的需要额外的代码来画出来，你可以打开这个激光武器单位的 xml 文件，把
它的绘图代码拷到武器代码的下面。（有时候会出现原来的武器的开火效果和新的武器的效
果并存，这应该也是绘图代码在作怪）
-----------------------------------------------------------------------------
关于武器修改的更多消息
游戏的所有武器都在 GlobalData/Weapon.xml 中保存。
就让我们来改一下海啸坦克的武器。
打开 Weapon.xml 文件，搜索 JapanAntiVehicleVehicleTech1Cannon，这是海啸坦克的武器
在这里的名称。
只需关注一些条目：
‘AttackRange=’攻击范围。
‘WeaponSpeed=’武器速度，其实是武器射出弹药的速度，对于激光类武器来说，很快，导
弹类则很慢。
‘AcceptableAimDelta=’武器的最大攻击角度。与一个单位的炮塔是如何定义的有关。增加这
个可以使武器开火更快，但是炮塔的动作将变得很丑。
‘ClipSize=’可以用在爆发型武器（应该指动员兵或是双刃那样）和弹药（应该是轰炸机）。
对于没有弹药限制的单位，你可以把这个设的大一些，让武器在爆发模式下更持久。
‘AutoReloadsClip=’告诉你武器是自动重装还是有限需要回去补充。‘AUTO’表示没有弹药限
制，‘RETURN_TO_BASE’表示单位要回去补充弹药。
‘Flags=’ 例如”ATTACK_NEEDS_LINE_OF_SIGHT”，表示武器开火需要看到目标。
‘CanFireWhileMoving=’表示武器是否可以运动中开火。
‘RequiredAntiMask=’过滤目标，使得武器只能攻击制定类型的目标。例如
RequiredAntiMask=”ANTI_WATER ANTI_GROUND ANTI_STRUCTURE”武器将会射击任何
在水面上，陆地上的单位和建筑，但是，不能对空和反潜。
‘FiringDuration=’武器开火持续时间，经常被用在不同持续时间的武器开火动作上。
‘ClipReloadTime=’开火的准确速率。降低以使武器更快，但一定要在‘FiringDuration’之上，
这样动作才能正常进行。
‘<Nuggets>’ 子段定义了武器的弹头和抛射物。
懂得其工作机理很重要。
武器其实并不造成伤害，他只是以一定速率发射出了抛射物，抛射物带着弹头到达目标，然
后弹头来造成伤害。
所 以 说 ， 武 器 造 成 了 伤 害 是 技 术 上 的 错 误 。 海 啸 武 器 的 弹 头 被 称 为
‘JapanAntiVehicleVehicleTech1Warhead’.
来看看我们可以改些什么。
首先，弹头有自己的‘RequiredAntiMask’，这个理论上必须匹配武器的‘RequiredAntiMask’中
的一个。但如果你想进一步做些什么，这也不是强制的。然后，我们找到‘DamageNugget’，
它掌握着弹头所能造成的伤害。
改变‘Damage=’来改变弹头的伤害。
‘DamageType=’定义了伤害的类型，与护甲类型一起使用，来造成不同的伤害。
‘DeathType=’代表单位在弹头下的死亡方式，只有很少的死亡类型。
‘SuppressionNugget’ 表 示 弹 头 的 区 域 压 制 效 果 。 ‘Radius=’ 表 示 压 制 的 范 围 ，
‘DurationSeconds=’表示压制持续时间，单位为秒。
这就是关于武器的一切，随心所欲的修改吧。
感谢 Overmind 提供的教程。
--------------------------------------------------------
为单位或者建筑添加维修工蜂
随便找个单位或者建筑物，就拿我们的坦克也行，打开其 xml 文件向下拖直到你 找到了
behaviors 的起始标签(看起来像<Behaviors> 后面跟着</Draws>)，也可以使用搜索功能来
找。一旦你定位了，复制粘贴下面的代码到 behaviors 的开始标签<Behaviors>和结束标签
</Behaviors>之间的任意部分。
<AssignSlavesTargetObjectSpecialPower
id=”ModuleTag_SpecialPowerRepairVehicle”
SpecialPowerTemplate=”SpecialPower_TargetedRepairVehicle” />
<SpawnBehavior
id=”ModuleTag_SpawnRepairDrones”
SpawnNumberData=”3″
InitialBurst=”3
SpawnReplaceDelayData=”10s”
SpawnedRequireSpawner=”true”
KillSpawnsOnCaptured=”true”
SpawnInsideBuilding=”true”
KillSpawnsOnDisabled=”true”>
<Die
DeathTypes=”ALL” />
<SpawnTemplate>AlliedWarFactoryRepairDrone</SpawnTemplate>
</SpawnBehavior>
改变下划线部分的值，分别来确定维修工蜂的总个数和该单位被制造出来时产生的工蜂个
数。
-----------------------------------------------------------------------------------------
如何编辑单位经验等级
要改变单位的 XP 等级，要去 GlobalData/ExperienceLevels.xml 文件。
There you can edit the XP values for all units.
这里你可以修改所有单位的经验值。如果你加入了新单位，你要把它们也加入到这个文件里，
这样它们才能升级。
现在我们来谈谈这个文件。
最开始，定义了一般的老兵级别 veterancy levels (VLs)。.
别改变它们，除非你为一个新的老兵系统增加了视觉效果。
所有单位初始级别是 1，而 2，3，4，分别对应老兵等级的 1，2，3 （veterancy levels 1 2
and 3）
我称它们为有经验的，老兵，精英（‘experienced’, ‘veteran’ and ‘elite’），EA 称它们为老兵，
精英，英雄（‘veteran’ ‘elite’ and ‘heroic’），名称无所谓，所以我用 LV1 LV2 LV3 来代替。
现在来看看它们怎么运作的，其实很简单。
这是从 ExperienceLevels.xml 中提取的盟军海豚的经验代码：
等级 1
<ExperienceLevelTemplate
id=”AlliedAntiNavalScoutExperienceLevel_1″
inheritFrom=”ExperienceLevel_AlliedRank1″
RequiredExperience=”1″
ExperienceAward=”750″>
<Target>AlliedAntiNavalScout</Target>
</ExperienceLevelTemplate>
等级 2
<ExperienceLevelTemplate
id=”AlliedAntiNavalScoutExperienceLevel_2″
inheritFrom=”ExperienceLevel_AlliedRank2″
Prerequisite=”AlliedAntiNavalScoutExperienceLevel_1″
RequiredExperience=”2250″
ExperienceAward=”1500″>
<Target>AlliedAntiNavalScout</Target>
</ExperienceLevelTemplate>
等级 3
<ExperienceLevelTemplate
id=”AlliedAntiNavalScoutExperienceLevel_3″
inheritFrom=”ExperienceLevel_AlliedRank3″
Prerequisite=”AlliedAntiNavalScoutExperienceLevel_2″
RequiredExperience=”4500″
ExperienceAward=”2250″>
<Target>AlliedAntiNavalScout</Target>
</ExperienceLevelTemplate>
等级 4
<ExperienceLevelTemplate
id=”AlliedAntiNavalScoutExperienceLevel_4″
inheritFrom=”ExperienceLevel_AlliedRank4″
Prerequisite=”AlliedAntiNavalScoutExperienceLevel_3″
RequiredExperience=”6750″
ExperienceAward=”3000″>
<Target>AlliedAntiNavalScout</Target>
</ExperienceLevelTemplate>
The 4 templates define all 4 ranks of the unit: a default one (level 1) and the 3 promoted
versions.
四个经验模板（即从<<ExperienceLevelTemplate。。到</ExperienceLevelTemplate>是一
个经验模板）代表等级 1 到 4。
我们工作集中在两个标签上。
第一个‘RequiredExperience=’，定义了该等级的该单位需要多少经验才能升级。例如，盟军
海豚要 6750 的经验才能升到 LV3。
The second function: ‘ExperienceAward=’ gives the value of XP a unit will gain by killing the
current unit at it’s current level.
第二个‘ExperienceAward=’，定义了，该等级下的单位值多少经验。比如一个苏联潜艇宰了
一只 1 级海豚，得到 750 经验，宰了一只 3 级海豚，得到 3000 经验。
我一般会把单位的升级经验设为其造价 3 倍，本身经验则为造价本身。
随便设就行了，别太夸张。
------------------------------------------
如何改变特殊能力模板
特殊能力模板是游戏中最复杂也最强大的部分。
用这些模板，你基本上可以无所不能，但要小心，它们也不容易对付。
对应的文件是 GlobalData/SpecialPowerTemplates.xml.
从一个简单的例子开始：
<SpecialPowerTemplate
id=”SpecialPower_UnpackReplaceSelf”
TargetType=”LOCATION_AND_ANGLE”
NameOfVoiceNameToUseAsInitiateIntendToDoVoice=”VoiceDeploy”
RadiusCursorRadius=”1″
PreventConditions=”BOOBY_TRAPPED IS_BEING_DRAGGED SOLD”
Flags=”WATER_OK FOGGED_SHROUDED_CELLS_OK CANNOT_LEAVE_ENCLOSURE
CAN_NOT_BE_SCRAMBLED”
WaypointModeTerminal=”false” >
<GameDependency
id=”SpecialPower_UnpackReplaceSelf_GameDependency”
ForbiddenModelConditions=”UNPACKING”/>
</SpecialPowerTemplate>
上述代码是一个 MCV 的展开特殊能力. ‘id=’必须是第一无二的,以便我们以后使用这个模板.
‘TargetType=’是一个目标选择系统,定义了当前的支援/特殊能力可以作用的对象. 被 CAPS
的关键词是被硬编码的动作,不能被重定义,但是这里有很多,所以我们只需去学习使用.所
以,MCV 展开的目标可以使任何地点/多角度的方位.
‘NameOfVoiceNameToUseAsInitiateIntendToDoVoice’字段定义了该能力模板执行时所播放
的声音.这里的是 MCV 在展开时的音效.
‘RadiusCursorRadius=’影响你的光标的外形.对于一些支援能力,你的光标会变为一些不同的
形状(比如核弹).这个标签定义了在使用在这个能力时,你的光标如何显示.
‘PreventConditions=’这个很重要.一个情况过滤器,来判断特殊能力动作是否可执行.我们可
以看到,MCV 不能展开的情况被定义了.例如‘IS_BEING_DRAGGED’,这个情况指的是 MCV 被
天启的鱼叉捕获, ‘SOLD’指的是你买掉总部的时候,还想使用它的打包/部署功能.
‘Flags=’定义了其他的情况,这些情况被‘PreventConditions=’定义为限制条件.这个准确的保
证了在特定的情况下,事情会无误的发生.
比如, ‘WATER_OK’表示,MCV 可以在水面上展开.现在它当然可以按照缺省值来做,但在某些
情况下,最好你最好保证事情会按你想的发展.
‘GameDependency’另一个特殊的功能.在当前的情况下,来阻止模型错误的发生.
‘ForbiddenModelConditions=”UNPACKING”表示 MCV 已经在展开时,不能在执行展开/打包
动作.
现在我会给一个实实在在的修改例子.
我一直深恶痛疾的,EA 这个 2B 一直不做的就是铁幕根本不是真正的铁幕,很多东西仍能够作
用于这层神圣不可侵犯的护盾.
所以我要让铁幕重新雄起,就像在 2 代中一样,绝对的免疫.有两个点会影响它,我要修改的就
是缩小光线和超时空转换.
到缩小光线（shrink ray）的模板,如下:
<SpecialPowerTemplate
id=”SpecialPower_ShrinkRay”
ReloadTime=”10s”
TargetType=”OBJECT”
NameOfVoiceNameToUseAsInitiateIntendToDoVoice=”VoiceShrinkRay”
Flags=”NEEDS_OBJECT_FILTER CANNOT_LEAVE_ENCLOSURE”
WaypointModeTerminal=”false” >
<!– must have same object filter as AlliedSupportAircraftShrinkRay –>
<ObjectFilter
Rule=”ANY”
Include=”VEHICLE HUGE_VEHICLE TIME_BOMB”
Exclude=”AIRCRAFT”
StatusBitFlagsExclude=”SUBMERGED AIRBORNE_TARGET”>
</ObjectFilter>
</SpecialPowerTemplate>
我们感兴趣的就是‘ObjectFilter’(目标过滤器),定义了光线可以作用的对象.这里定义的内容
是:光线可以射载具,重型载具和时间炸弹,天上飞的和水下潜的它没辙.
现在我要让他在铁幕单位面前也阳痿不举.
于是我找到了硬编码的‘UNDER_IRON_CURTAIN’(铁幕之下)动作/特性条,以及铁幕的激活效
果‘IronCurtainEffect’
对缩小光线的操作如下:
<SpecialPowerTemplate
id=”SpecialPower_ShrinkRay”
ReloadTime=”10s”
TargetType=”OBJECT”
NameOfVoiceNameToUseAsInitiateIntendToDoVoice=”VoiceShrinkRay”
Flags=”NEEDS_OBJECT_FILTER CANNOT_LEAVE_ENCLOSURE”
WaypointModeTerminal=”false” >
<!– must have same object filter as AlliedSupportAircraftShrinkRay –>
<ObjectFilter
Rule=”ANY”
Include=”VEHICLE HUGE_VEHICLE TIME_BOMB”
Exclude=”AIRCRAFT”
StatusBitFlagsExclude=”SUBMERGED AIRBORNE_TARGET UNDER_IRON_CURTAIN”>
<ExcludeThing>IronCurtainEffect</ExcludeThing>
</ObjectFilter>
</SpecialPowerTemplate>
我要做的就是把‘UNDER_IRON_CURTAIN’加到例外情况里,这样光线在铁幕单位前就射不了
了.( StatusBitFlagsExclude=”SUBMERGED AIRBORNE_TARGET UNDER_IRON_CURTAIN”>)
‘ExcludeThing’也使得光线不能在铁幕效果生效时发射(例如,我正好激活了一个铁幕),同样,
对 超 时 空 转 换 , 我 也 这 样 做 了 , 铁 幕 单 位 不 会 再 被 超 时 空 转 换 推 倒 了 .
（<ExcludeThing>IronCurtainEffect</ExcludeThing>）
现在再给一个例子,让你更深入了解特殊能力模板的工作机制.
我将解说超时空换位怎样发生.
<SpecialPowerTemplate
id=”SpecialPowerChronoSwapTeleport”
ReloadTime=”120s”
TargetType=”OBJECT”
EvaEventToPlayWhenSelectingTarget=”SelectUnit”
inheritFrom=”SpecialPowerChrono_Base”
RequiredPlayerTech=”PlayerTech_Allied_ChronoSwap”>
<ObjectFilter
Rule=”ANY”
Relationship=”ALLIES”
Include=”INFANTRY VEHICLE TIME_BOMB”
Exclude=”AIRCRAFT”
StatusBitFlagsExclude=”SUBMERGED AIRBORNE_TARGET NOT_IN_WORLD”>
<IncludeThing>AlliedTimeBombLvl1</IncludeThing>
<IncludeThing>AlliedTimeBombLvl2</IncludeThing>
<IncludeThing>AlliedTimeBombLvl3</IncludeThing>
</ObjectFilter>
<GameDependency
id=”Allied_ChronoSwapTeleport_GameDependency”>
<RequiredObject>AlliedConstructionYard</RequiredObject>
</GameDependency>
</SpecialPowerTemplate>
‘TargetType=”OBJECT”表示在用这个能力时,我们必须选择一个单位.
‘EvaEventToPlayWhenSelectingTarget=’表示在你选择该单位时播放的 EVA 大妈的声音.
‘nheritFrom=’在源代码中被广泛使用.意味着定义的对象或是模板使用了一些别处定义的基
础特性.在当前情况下,表示超时空换位是一个基于超时空技术的能力.
‘Relationship= 表 示 能 力 是 否 可 用 于 自 己 单 位 , 敌 人 , 还 是 两 者 皆 可 . 在 这 种 情 况 , 是
“ALLIES”(并非的盟军阵营(Allied),而是指你自己的单位或是友军),这样能力只作用于你的单
位.
该能力,如你所见,将作用于步兵,载具和时间炸弹,对天上飞的和水下藏的无能为力.
‘IncludeThing’确保该能力能够作用于时间炸弹,其实是多余的,因为炸弹被单独的另外定义
了.
最后的过滤器‘RequiredObject’是一个附属,告诉你要有总部才能使用该能力.
10.机密协议相关解释
PlayerTemplates.xml
<PlayerTemplate
id=" Allies"
Side=" Allies"
Type="PLAYABLE"
ParachuteOCL=" OCL_AlliedParachute"
DefaultTech="PlayerTech_ Allied"调用玩家科技
PlayerTechUpgradeBinding=" PlayerTechUpgradeBinding_Allied"调用绑定科技
升级类型的科技，比如给战机多加弹药
……
PlayerTechStoreTemplates.xml
玩家科技存储模板
<PlayerTechStoreTemplate
id="PlayerTechStore_Allied"
Faction="Allies">
<Row>行
<Button>Purchase_PlayerTech_Allied_PrecisionStrike</Button>
<Button>Purchase_PlayerTech_Allied_Paradrop_Rank1</Button>
<Button>Purchase_PlayerTech_Allied_ChronoSwap</Button>
</Row>
</PlayerTechStoreTemplate>
ButtonStateDataCommon.xml
<ButtonSingleStateData id="ButtonStateCampaignPlayerPowerParadropLvl1">
<State
Image="Button_PlayerPower_Paradrop1"
Title="NAME:CampaignPlayerPowerParadropLvl1"
TypeDescription="TYPE:CampaignPlayerPowerParadropLvl1"
Description="DESC:CampaignPlayerPowerParadropLvl1" />
</ButtonSingleStateData>
AlliedAirMarshall.xmlAI 进攻能力
<PowerChoice
PlayerPower=" PlayerTech_Allied_Paradrop_Rank1" Weight="300%"/>
AlliedCoopBasePersonality.xmlAI 进攻能力
<PowerChoice
PlayerPower=" PlayerTech_Allied_Paradrop_Rank1" Weight="300%"/>
AlliedSoloBasePersonality.xmlAI 进攻能力
<PowerChoice
PlayerPower=" PlayerTech_Allied_Paradrop_Rank1" Weight="300%"/>
玩家科技
PlayerTechs.xml
<PlayerTech
id="PlayerTech_ Allied"/>
<PlayerTech
id="PlayerTech_Allied_Paradrop_Rank1"
TechPointsRequired="1">
<TechDependency>PlayerTech_Allied_HighTechnology</TechDependency>条件
</PlayerTech>
PlayerTechStoreTemplates.xml
购买玩家科技按键模板
<PurchasePlayerTechButtonTemplate
id="Purchase_PlayerTech_Allied_Paradrop_Rank1"
PlayerTech="PlayerTech_Allied_Paradrop_Rank1"调用由秘密科技购买
StateData="ButtonStateCampaignPlayerPowerParadropLvl1"/>调用单一按键数据声明
ButtonTemplates.xml 游戏杆控制模板
<JoypadCommandBarButtonTemplate
id="ButtonCampaignPlayerPoweParadrop_Rank1">
<Data>
<PlayerTargetedPower
StateData="ButtonStateCampaignPlayerPowerParadropLvl1"
SpecialPower="SpecialPowerParadropLvl1"
RadiusCursor="Target_Allied_Paradrop"/>
</Data>
</JoypadCommandBarButtonTemplate>
PlayerPowerButtonTemplates.xml 玩家技能按键模板
<PlayerPowerButtonTemplate
id="ButtonCampaignPlayerPoweParadrop_Rank1"
SpecialPower="SpecialPowerParadropLvl1">
<Data>
<TargetedPower 目标技能
RadiusCursor="Target_Allied_Paradrop"
StateData="ButtonStateCampaignPlayerPowerParadropLvl1"/>
</Data>
</PlayerPowerButtonTemplate>
SpecialPowerTemplates.xml
<SpecialPowerTemplate
id="SpecialPower_EjectPassengers"
ReloadTime="10s"
TargetType="LOCATION"
RadiusCursorRadius="60"
NameOfVoiceNameToUseAsInitiateIntendToDoVoice="VoiceEject"
Flags="LIMIT_DISTANCE FOGGED_SHROUDED_CELLS_OK
CANNOT_LEAVE_ENCLOSURE NOT_ON_OBSTACLES CAN_NOT_BE_SCRAMBLED"
MinCastRange="15"
WaypointModeTerminal="false"/>
CAMP_AlliedBomberAircraft_Infantry_2.xml
被调用的飞机单位
<GameObject
id="CAMP_AlliedBomberAircraft_Infantry_2"
inheritFrom="AlliedBomberAircraft"
<Behaviors>
<TransportContain id="ModuleTag_Contain" xai:joinAction="Append">
<InitialPayload Name="AlliedScoutInfantry"乘坐的兵种
Count="1" />
<InitialPayload Name="AlliedAntiInfantryInfantry"
Count="3" />
<InitialPayload Name="AlliedAntiVehicleInfantry"
Count="1" /> </TransportContain>
<SpecialPower 特殊能力
id="ModuleTag_EjectPassengers"
xai:joinAction="Replace"
SpecialPowerTemplate="SpecialPower_EjectPassengers"调用运客能力
UpdateModuleStartsAttack="true" />
<EjectPassengersSpecialAbilityUpdate 释放乘客的能力
id="ModuleTag_EjectPassengersUpdate"
xai:joinAction="Replace"
SpecialPowerTemplate="SpecialPower_EjectPassengers"调用运客能力
Height="150.0"
StartAbilityRange="0.0"
TimePerPassenger=".5s"
Radius="0"
RunOffMapWhenDone="true"飞出地图外
IgnoreTargetLocation="true"
Options="RECONSTITUTE_STORED_COMMAND DO_NOT_DO_AI_SPECIAL_POWER"/>
<RunOffMapBehavior 从地图外飞进来
id="ModuleTag_RunOffMapBehavior"
xai:joinAction="Replace"
FlyingOffMap="true"
RequiresSpecificTrigger="true" />
<WeaponSetUpdate
id="ModuleTag_WeaponSetUpdate"
xai:joinAction="Remove"/>武器行为=释放
CommandData.xml 逻辑支配
<LogicCommand
Options="NEED_TARGET_POS"
Type="SPECIAL_POWER"
id="Command_ParadropLvl1"> <SpecialPower>SpecialPowerParadropLvl1</SpecialPower>调用空降特殊
技能
<AISpecialPowerInfo
Heuristic="PLAYER_AOE_BUFF"
Manager="SKIRMISH_AI"
TargetObjectInclude="CAN_ATTACK"
MinTargetsHit="1"
MinEnemiesNearby="5">
</AISpecialPowerInfo>
</LogicCommand>
SpecialPowerTemplates.xml
<SpecialPowerTemplate
id="SpecialPowerParadropLvl1"
ReloadTime="300s"
TargetType="LOCATION"
EvaEventToPlayWhenSelectingTarget="SelectSpecialPowerTargetArea"
RadiusCursorRadius="100"
Flags="IS_PLAYER_POWER PATHABLE_ONLY NOT_CLIFF_CELL
NO_FORBIDDEN_OBJECTS"
RequiredPlayerTech="PlayerTech_Allied_Paradrop_Rank1"秘密科技条件
WaypointModeTerminal="false" >
<ForbiddenObjectFilter
Rule="ANY"
Include="STRUCTURE CRUSHABLE_OBSTACLE AIRCRAFT"
Exclude="BRIDGE_ENDCAP BRIDGE_SEGMENT">
<ExcludeThing>NanoSwarmHiveEffect</ExcludeThing>纳米蜂房不可以降落
</ForbiddenObjectFilter>
<GameDependency
id="Allied_Paradrop_Rank1_GameDependency">
<RequiredObject>AlliedConstructionYard</RequiredObject>条件
</GameDependency>
<ForbiddenPlayerTech>PlayerTech_Allied_Paradrop_Rank2</ForbiddenPlayerTech>条件
<ForbiddenPlayerTech>PlayerTech_Allied_Paradrop_Rank3</ForbiddenPlayerTech>条件
</SpecialPowerTemplate>
SpecialPowerTemplates.xml
<SpecialPowerTemplate
id="SpecialPower_EjectPassengersUntargeted"
ReloadTime="10s"
TargetType="NONE"没有目标
Flags="CAN_NOT_BE_SCRAMBLED" 不被干扰
NameOfVoiceNameToUseAsInitiateIntendToDoVoice="VoiceEvacuate"
WaypointModeTerminal="false"/>
物体建立列表，属于最底层
ObjectCreationLists.xml
<ObjectCreationList
id="OCL_ParaDropLvl1">
<CreateObject
Options="IGNORE_ALL_OBJECTS DONT_SET_PRODUCER ISSUE_MOVE_AFTER_CREATION
FIRE_SPECIAL_POWER MOVE_TARGET_USES_OFFSET ORIENT_TOWARD_MOVE_DESTINATION
CREATE_AT_TARGET"
Disposition="LIKE_EXISTING"部署=像乘坐出租车
FireSpecialPowerTemplate="SpecialPower_EjectPassengers">开火特殊模板
<Offset x="0" y="0" z="190"/>
<CreateObject>CAMP_AlliedBomberAircraft_Infantry_2</CreateObject>调用的飞机
</CreateObject>
</ObjectCreationList>
CommandData.xml 逻辑支配
<LogicCommandSet
id="PlayerSpellBookCommandSet">
<!-- Allies Powers -->
<Cmd>Command_SelectObjectsForChrono</Cmd>
<Cmd>Command_ParticleCannonSuperWeapon</Cmd>
<Cmd>Command_PrecisionStrike</Cmd>
<Cmd>Command_SatelliteSweep</Cmd>
<Cmd> Command_ParadropLvl1</Cmd>调用逻辑支配
</LogicCommandSet>
ObjectCreationLists.xml
物体建立列表，用于标示目的地
<ObjectCreationList
id="OCL_PrecisionStrikeBeacon">
<CreateObject
Options="IGNORE_ALL_OBJECTS CREATE_AT_TARGET"
Disposition="ON_GROUND_ALIGNED USE_WATER_SURFACE"
DispositionIntensity="50"
DispositionAngle="72d"
Count="1">
<CreateObject>AlliedPrecisionStrikeBeacon</CreateObject>建造精确打击目标物体
</CreateObject>
</ObjectCreationList>
PlayerSpellBook.xml
某个单位，比如步兵，坦克，这里是被机密武器调用，属于顶级调用
<GameObject
id="PlayerSpellBook"
inheritFrom="PlayerSpellBook"
CommandSet="PlayerSpellBookCommandSet"调用逻辑支配设置
xai:joinAction="Append">
<Behaviors>
玩家技能管理
<PlayerPowerManager
id="ModuleTag_PlayerPowerManager_ParadropLvl1"
SpecialPowerTemplate="SpecialPowerParadropLvl1"调用特殊技能
/>
物体建造列表
<OCLSpecialPower
id="ModuleTag_ParadropLvl1"
SpecialPowerTemplate="SpecialPowerParadropLvl1"调用特殊技能
UpdateModuleStartsAttack="false"
AvailableAtStart="true"是否开始就能使用
OCL="OCL_ParaDropLvl1"调用 OCL（物体建立列表）
DestinationOCL="OCL_PrecisionStrikeBeacon"调用 OCL 目的地
CreateLocation="CREATE_AT_OFFSET_FROM_TARGET_ALONG_SECONDARY_OBJECT_VECTOR
_AND_MOVE_TO_TARGET"
CreateLocationOffset="1000.0">
<NearestSecondaryObjectFilter
Relationship="SAME_PLAYER">
<IncludeThing>AlliedConstructionYard</IncludeThing>调用主基地
</NearestSecondaryObjectFilter>
</OCLSpecialPower>
</Behaviors>
</GameObject>
感谢本文作者及翻译者