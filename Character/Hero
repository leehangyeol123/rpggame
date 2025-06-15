package Character;

public class Hero {
	public String name;
	public int level = 1;
	public int hp = 100;
	public int mp = 50;
	public int power = 10;
	public int defense = 10;
	public int experience = 0;
	public int money = 0;
	public boolean isAdvanced = false;

	public String weapon = null;
	public int weaponPower = 0;

	public Hero(String name) {
		this.name = name;
	}

	// 복사 생성자 (전직 클래스에서 호출)
	public Hero(Hero other) {
		this.name = other.name;
		this.level = other.level;
		this.hp = other.hp;
		this.mp = other.mp;
		this.power = other.power;
		this.defense = other.defense;
		this.experience = other.experience;
		this.money = other.money;
		this.weapon = other.weapon;
		this.isAdvanced = true;
	}

	public int attack() {
		return level * 10 + power * 2;
	}

	public void attacked(int damage) {
		int real = Math.max(0, damage - defense);
		hp -= real;
		if (hp < 0)
			hp = 0;
		System.out.printf("%s이(가) %d의 피해를 입었습니다. HP: %d\n", name, real, hp);
	}

	public Hero levelUp() {
		while (experience >= level * 2) {
			experience -= level * 2;
			level++;
			money += 100;
			hp = 100 + (level - 1) * 30;
			mp = 50 + (level - 1) * 10;
			System.out.printf("레벨업! 현재 레벨: %d\n", level);

			if (level == 10 && !isAdvanced) {
				return promote();
			}
		}
		return this;
	}

	public Hero promote() {
		return this;
	}

	public void attackEffect(Monster m) {
		// 기본은 없음
	}

	public void printAvailableSkills() {
		System.out.println("1. 스킬1 (Lv3, MP10)");
		System.out.println("2. 스킬2 (Lv5, MP15)");
		System.out.println("3. 스킬3 (Lv10, MP40)");
	}

	public boolean useSkill(int num, Monster m) {
		return false;
	}
}
