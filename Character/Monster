package Character;

public abstract class Monster extends Character {
	public int power;
	public int defense;
	public int money;
	public int experience;

	@Override
	public int attack() {
		return level * 10 + power;
	}

	@Override
	public void attacked(int damage) {
		int real = Math.max(0, damage - defense);
		hp -= real;
		System.out.printf("%s이(가) %d의 피해를 입었습니다. HP: %d\n", name, real, hp);
	}
}
