# The Shapley value

## General Idea

目的:

用于评价一次结果中不同特征的对结果的影响程度

场景:

a,b,c 三个人的工作效率分别是 2,1,3, 同时三人合作时的效率是10. 因为合作有促进或妨碍效果, 此时不能简单的按照 2:1:3 的比例计算每个人的工作效率.

## the shapley value

The Shapley value 本是用于评价
由多个玩家（player）共同参与的博弈（game），当参与博弈的玩家不同，所获得的奖励也有所不同，部分玩家在这场博弈中会有较大的贡献，而部分玩家则贡献较小。

Shapley value是一个能够根据不同玩家的贡献，通过计算 *平均边际贡献*, 将总的奖励公平地分配给每个玩家的度量指标。

对于员工 c, 通过比较其他人与其合作后效率的变化来获得其 *平均边际贡献*

|原组 -> 新组|原效率|新效率| 变化 |
|----|----|----|----|----|
|{} -> {c} |  0  |  3  |  3 |
|{a} -> {a,c} |  2  |  7  |  5 |
|{b} -> {b,c} |  1  |  5  |  4 |
|{a,b} -> {a,b,c} |  5  |  10  |  5 |

c 的shapley value 则为 

$$\frac{1}{3}(\frac{3}{C^0_2} + \frac{5}{C^1_2} + \frac{4}{C^1_2} + \frac{5}{C^2_2}) = \frac{25}{6}$$

### properties

Shapley Value 是满足 Efficiency,Symmetry, Dummy 和 Additivity 的唯一贡献量化指标。

Dummy：如果一个玩家对于任何他参与的博弈都没有贡献，则他的 Shapley Value 为0。

Symmetry：对于任意两个成员 i、j, 若任意其他团体与其中一人合作后团体贡献变化一致, 则i和j的Shapley value 相等 。

Efficiency：所有成员的Shapley Value 之和等于总奖励. 保证每个人都能按其 Shapley value 分得奖励,同时没有冗余或不足。

Linearity：若有一场博弈u的奖励总可以表示为两个小博弈v, w 之和,则对于任意玩家i，其在博弈u中的Shapley value可以表示为其在另外两场博弈中的Shapley value之和。

### advantages

由 Efficiency, 可以保证公平的分配结果, 而其他模型无法保证, 例如 LIME拟合出的模型存在bias时, bias的贡献无法分配

Shapley Value 的计算不受限于局部范围, 可以在全局范围对比不同数据

Shapley Value 是唯一拥有上述四个性质的指标, 有牢固的理论基础却对模型本身没有任何假设

### disadvantages

1. 计算量大, 特征数较多时只能通过随机采样的方式计算

2. Shapley Value 是为分配而非预测设计的, 所以不能像其他拟合解释模型一样进行预测

3. 实际部分变量是相关的, 而在模拟数据时因为无法得知关联性, 所以对特征的是独立采样的, 可能采样到不存在的样例

有许多针对 Shapley Value 的缺点进行改进的方法, 虽然失去了部分重要性质但是却从实用性得到了增强,  比如 SHAP 就包含大量针对计算性\解释性以及预测的改进
