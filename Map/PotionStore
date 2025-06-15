package Map;

import java.util.Scanner;

import Character.Hero;

public class PotionStore {
	public static void open(Hero h, Scanner sc) {
		System.out.println("1. 힘 +3 (30G), 2. 방어 +3 (30G), 3. 경험치 +50 (100G), 4. HP +50 (10G), 5. 복불복 (50G)");
		int choice = sc.nextInt();

		switch (choice) {
		case 1 -> apply(h, "power", 3, 30);
		case 2 -> apply(h, "defense", 3, 30);
		case 3 -> apply(h, "exp", 50, 100);
		case 4 -> apply(h, "hp", 50, 10);
		case 5 -> gamble(h, 50);
		default -> System.out.println("잘못된 입력");
		}
	}

	static void apply(Hero h, String stat, int amount, int cost) {
		if (h.money >= cost) {
			switch (stat) {
			case "power" -> h.power += amount;
			case "defense" -> h.defense += amount;
			case "exp" -> h.experience += amount;
			case "hp" -> h.hp += amount;
			}
			h.money -= cost;
			System.out.println(stat + " 상승!");
		} else {
			System.out.println("돈이 부족함");
		}
	}

	static void gamble(Hero h, int cost) {
		if (h.money < cost) {
			System.out.println("돈이 부족함");
			return;
		}
		int dice = (int) (Math.random() * 6);
		if (dice > 3) {
			h.power += 3;
			h.defense += 3;
			System.out.println("운 좋음! 능력치 상승!");
		} else {
			h.power -= 3;
			h.defense -= 3;
			System.out.println("능력치 하락 ㅠㅠ");
		}
		h.money -= cost;
	}
}
