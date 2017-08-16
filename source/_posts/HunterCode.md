---
title: Hunter Code
---
Welcome to [Hunter for Lrony Blog](https://lrony.github.io/)!  Hunter WebUrl is [LOLHunter](http://www.lolhunter.cn).

<div class="tip">
    需要注意的是,本文中所有代码块为临时编写使用,无法在正式项目中使用.也无法编译通过！
</div>

### Start

### Start for ALL API
``` java
// API
{
	// My Type
	{
		// 位置类型
		pos {
			int x, int y
		};
	}

	// 获取红色防御塔位置
	public boolean getRedTower(pos p);
	// 获取蓝色防御塔位置
	public boolean getBlueTower();
	// 当前是否在危险区域
	public boolean isDangerZone();
	// 当前是否残血
	public boolean isSmallBlood();
	// 获取红色英雄数量以及位置
	public boolean getRedHero(int num, pos p);
	// 获取蓝色英雄数量
	public boolean getBlueHero(int num);
	// 获取红色小兵数量以及位置
	public boolean getRedMobs(int num, pos p);
	// 获取红色小兵数量
	public boolean getBlueMobs(int num);
	// 进攻
	public void Attack(x, y);
}
```
### End for ALL API

### Start for 对战逻辑

``` java
// By Hunter for Lrony
// 2017.08.15
{
	// Code
	{
		boolean haveRedTower, haveBlueTower;
		boolean isDangerZone;
		boolean haveRedHero, haveBlueHero;
		pos redHeroPos, redTowerPos;
		int redHeroNum, blueHeroNum;
		boolean haveRedMobs, haveBlueMobs;
		pos redMobsPos;
		int redMobsNum, blueMobsNum;

		isDangerZone = isDangerZone();
		haveRedTower = getRedTower(redTowerPos);
		haveBlueTower = getBlueTower();
		isSmallBlood = isSmallBlood();
		haveRedHero = getRedHero(redHeroNum, redHeroPos);
		haveBlueHero = getRedHero(blueHeroNum);
		haveRedMobs = getRedMobs(redMobsNum, redMobsPos);
		haveBlueMobs = getBlueMobs(blueMobsNum);

		// check is need return
		{
			// must return
			if (isDangerZone) {
				return;
			}
			if (isSmallBlood) {
				>> back home
				return;
			}

			// other
			if (haveRedTower) {
				if (haveRedHero) {
					return;
				}
				if (blueMobsNum <= 0) {
					return;
				}
				if (redMobsNum - blueMobsNum > 3) {
					return;
				}
			}

			if (haveRedHero) {
				int i = redHeroNum - blueHeroNum;
				if (i > 1 || haveBlueTower = false) {
					return;
				}
			}
		}

		// attack
		{
			if (haveRedHero) {
				Attack(redHeroPos.x, redHeroPos.y);
				return;
			}
			if (haveRedTower) {
				Attack(redTowerPos.x, redTowerPos.y);
				return;
			}
			if (haveRedMobs) {
				Attack(redMobsPos.x, redMobsPos.y);
				return;
			}
		}	
	}
}
```
### End for 对战逻辑

### Contact information
QQ: 29682909
Email: 29682909@qq.com

### End