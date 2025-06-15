package Main;

import java.util.Scanner;

import Character.Archer;
import Character.Boar;
import Character.Dog;
import Character.Hero;
import Character.Mage;
import Character.Monster;
import Character.Racoon;
import Character.Warrior;
import Character.WildCat;
import Map.Mission;
import Map.PotionStore;
import Map.WeaponStore;

public class RpgGameMain {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Hero hero = null;

		System.out.println("직업 선택: 1. 전사  2. 마법사  3. 궁수");
		int job = sc.nextInt();
		System.out.print("이름 입력: ");
		String name = sc.next();

		switch (job) {
		case 1:
			hero = new Warrior(name);
			break;
		case 2:
			hero = new Mage(name);
			break;
		case 3:
			hero = new Archer(name);
			break;
		default:
			System.out.println("잘못된 선택입니다.");
			return;
		}

		while (true) {
			heroStatus(hero);
			System.out.println("\n[1] 사냥터  [2] 포션상점  [3] 무기상점  [4] 종료");
			int menu = sc.nextInt();

			switch (menu) {
			case 1: {
				boolean isResurrected = false;
				System.out.println("1. 너구리  2. 살쾡이  3. 들개  4. 맷돼지");
				int sel = sc.nextInt();
				Monster m = null;

				switch (sel) {
				case 1:
					m = new Racoon();
					break;
				case 2:
					m = new WildCat();
					break;
				case 3:
					m = new Dog();
					break;
				case 4:
					m = new Boar();
					break;
				default:
					System.out.println("잘못된 선택입니다.");
					continue;
				}

				while (hero.hp > 0 && m.hp > 0) {
					System.out.printf("\n%s의 턴입니다.\n", hero.name);
					System.out.println("1. 기본 공격");
					System.out.println("2. 스킬 사용");
					System.out.print("행동 선택: ");
					int act = sc.nextInt();

					if (act == 1) {
						hero.attackEffect(m);
						if (m.hp > 0) {
							int damage = hero.attack();
							m.attacked(damage);
						}
					} else if (act == 2) {
						hero.printAvailableSkills();
						System.out.print("스킬 번호 입력: ");
						int skillNum = sc.nextInt();
						boolean success = hero.useSkill(skillNum, m);
						if (!success)
							continue;
					} else {
						System.out.println("잘못된 입력입니다.");
						continue;
					}

					if (m.hp <= 0) {
						System.out.println("몬스터 처치!");
						hero.money += m.money;
						hero.experience += m.experience;
						Mission.reward(hero, m.name);

						Hero promoted = hero.levelUp();
						if (promoted != hero) {
							hero = promoted; // 전직 시 교체
						}
						break;
					}

					System.out.printf("%s의 반격!\n", m.name);
					hero.attacked(m.attack());

					if (hero.hp <= 0) {
						if (!isResurrected) {
							System.out.println("사망... 부활합니다 (HP 1)");
							hero.hp = 1;
							isResurrected = true;
						} else {
							System.out.println("전투에서 패배했습니다. 메인 메뉴로 돌아갑니다.");
							break;
						}
					}
				}
				break;
			}
			case 2:
				PotionStore.open(hero, sc);
				break;

			case 3:
				WeaponStore.open(hero, sc);
				break;

			case 4:
				System.out.println("게임을 종료합니다.");
				return;

			default:
				System.out.println("잘못된 선택입니다.");
				break;
			}
		}
	}

	public static void heroStatus(Hero h) {
		System.out.println("******************************");
		System.out.printf("현재 영웅 이름 : %s\n", h.name);
		System.out.printf("레벨 : %d\n", h.level);
		System.out.printf("힘 : %d\n", h.power);
		System.out.printf("방어력 : %d\n", h.defense);
		System.out.printf("HP : %d\n", h.hp);
		System.out.printf("MP : %d\n", h.mp);
		System.out.printf("경험치 : %d\n", h.experience);
		System.out.printf("돈 : %d원\n", h.money);
		System.out.println("******************************");
	}
}
