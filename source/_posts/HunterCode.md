---
title: Hunter Code
---
Welcome to [Hunter for Lrony Blog](https://lrony.github.io/)!  Hunter WebUrl is [LOLHunter](http://www.lolhunter.cn).

<div class="tip">
    需要注意的是,该段代码块为临时编写使用,无法在正式项目中使用.也无法编译通过！
</div>

### Start

``` java
// By Hunter for Lrony
// 2017.08.15
{
	// API
	{
		// My Type
		{
			pos {
				int x, int y
			};
		}

		public boolean getRedTower(pos p);
		public boolean getBlueTower();
		public boolean isDangerZone();
		public boolean isSmallBlood();
		public boolean getRedHero(int num, pos p);
		public boolean getBlueHero(int num);
		public boolean getRedMobs(int num, pos p);
		public boolean getBlueMobs(int num);
		public void Attack(x, y);
	}

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
### Contact information
QQ: 29682909
Email: 29682909@qq.com

### End