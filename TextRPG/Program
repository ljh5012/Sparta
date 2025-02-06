# Sparta
using System;

class Program
{

    static int playerGold = 1500;
    static Dictionary<int, (string Name, string Type, int Value, bool Equipped, bool Purchased)> items = new Dictionary<int, (string, string, int, bool, bool)>
    {
        { 1, ("무쇠갑옷", "방어력", 5, true, true) },
        { 2, ("스파르타의 창", "공격력", 7, true, true) },
        { 3, ("낡은 검", "공격력", 2, false, false) }
    };

    static Dictionary<int, (string Name, string Type, int Value, int Price, bool Purchased)> shopItems = new Dictionary<int, (string, string, int, int, bool)>
    {
        { 1, ("수련자 갑옷", "방어력", 5, 1000, false) },
        { 2, ("무쇠갑옷", "방어력", 9, 0, true) },
        { 3, ("스파르타의 갑옷", "방어력", 15, 3500, false) },
        { 4, ("낡은 검", "공격력", 2, 600, false) },
        { 5, ("청동 도끼", "공격력", 5, 1500, false) },
        { 6, ("스파르타의 창", "공격력", 7, 0, true) }
    };





    static void Main()
    {
        while (true)
        {
            MainScene();
        }
    }

    static void MainScene()
    {
        Console.Clear();
        Console.WriteLine("스파르타 마을에 오신 여러분 환영합니다.\n");
        Console.WriteLine("이곳에서 던전으로 들어가기 전 활동을 할 수 있습니다.\n");
        Console.WriteLine("1. 상태 보기");
        Console.WriteLine("2. 인벤토리");
        Console.WriteLine("3. 상점\n");
        Console.Write("원하시는 행동을 입력해주세요.\n>> ");

        string input = Console.ReadLine();
        switch (input)
        {
            case "1":
                Status();
                break;
            case "2":
                Inventory();
                break;
            case "3":
                Shop();
                break;
            default:
                Console.WriteLine("잘못된 입력입니다.");
                Console.ReadKey();
                break;
        }
    }

    static void Status()
    {
        Console.Clear();
        int totalAttack = 10;
        int totalDefense = 5;

        foreach (var item in items.Values)
        {
            if (item.Equipped)
            {
                if (item.Type == "공격력") totalAttack += item.Value;
                if (item.Type == "방어력") totalDefense += item.Value;
            }
        }
        Console.WriteLine("상태 보기");
        Console.WriteLine("캐릭터의 정보가 표시됩니다.\n");
        Console.WriteLine("Lv. 01");
        Console.WriteLine("Chad ( 전사 )");
        Console.WriteLine($"공격력 : {totalAttack} ({(totalAttack > 10 ? "+" + (totalAttack - 10) : "")})");
        Console.WriteLine($"방어력 : {totalDefense} ({(totalDefense > 5 ? "+" + (totalDefense - 5) : "")})");
        Console.WriteLine("체 력 : 100");
        Console.WriteLine("Gold : 1500 G\n");
        Console.WriteLine("0. 나가기\n");
        Console.Write("원하시는 행동을 입력해주세요.\n>> ");

        while (Console.ReadLine() != "0")
        {
            Console.Write("잘못된 입력입니다. 다시 입력해주세요.\n>> ");
        }
    }

    static void Inventory()
    {
        while (true)
        {
            Console.Clear();
            Console.WriteLine("인벤토리");
            Console.WriteLine("보유 중인 아이템을 관리할 수 있습니다.\n");
            Console.WriteLine("[아이템 목록]\n");
            Console.WriteLine("1. 장착 관리");
            Console.WriteLine("0. 나가기\n");
            Console.Write("원하시는 행동을 입력해주세요.\n>> ");

            string input = Console.ReadLine();
            switch (input)
            {
                case "1":
                    Equipment();
                    break;
                case "0":
                    return;
                default:
                    Console.WriteLine("잘못된 입력입니다.");
                    Console.ReadKey();
                    break;
            }
        }
    }

    static void Equipment()
    {
        while (true)
        {
            Console.Clear();
            Console.WriteLine("인벤토리 - 장착 관리");
            Console.WriteLine("보유 중인 아이템을 관리할 수 있습니다.\n");
            Console.WriteLine("[아이템 목록]");
            foreach (var item in items)
            {
                Console.WriteLine($"- {item.Key} {(item.Value.Equipped ? "[E]" : "")} {item.Value.Name} | {item.Value.Type} +{item.Value.Value}");
            }
            Console.WriteLine("\n0. 나가기\n");
            Console.Write("원하시는 행동을 입력해주세요.\n>> ");

            string input = Console.ReadLine();
            if (input == "0") return;

            if (int.TryParse(input, out int choice) && items.ContainsKey(choice))
            {
                var item = items[choice];
                items[choice] = (item.Name, item.Type, item.Value, !item.Equipped, item.Purchased);
                Console.WriteLine(item.Equipped ? "장착을 해제했습니다." : "장착했습니다.");
            }
            else
            {
                Console.WriteLine("잘못된 입력입니다.");
            }
            
        }
    }

    static void Shop()
    {
        while (true)
        {
            Console.Clear();
            Console.WriteLine("상점");
            Console.WriteLine("필요한 아이템을 얻을 수 있는 상점입니다.\n");
            Console.WriteLine("[보유 골드] {0} G\n", playerGold);
            Console.WriteLine("[아이템 목록]");
            foreach (var item in shopItems)
            {
                Console.WriteLine("{0}. {1} | {2} +{3} | {4}",
                    item.Key,
                    item.Value.Name,
                    item.Value.Type,
                    item.Value.Value,
                    item.Value.Purchased ? "구매완료" : item.Value.Price + " G");
            }
            Console.WriteLine("\n1. 아이템 구매");
            Console.WriteLine("0. 나가기\n");
            Console.Write("원하시는 행동을 입력해주세요.\n>> ");

            string input = Console.ReadLine();
            if (input == "0") return;
            if (input == "1") BuyItem();
        }
    }

    static void BuyItem()
    {
        Console.Write("구매할 아이템 번호를 입력해주세요.\n>> ");
        
        if (!int.TryParse(Console.ReadLine(), out int choice) || !shopItems.ContainsKey(choice))
        {
            Console.WriteLine("잘못된 입력입니다.");
        }
        else
        {
            var item = shopItems[choice];
            if (item.Purchased)
            {
                Console.WriteLine("이미 구매한 아이템입니다.");
            }
            else if (playerGold >= item.Price)
            {
                playerGold -= item.Price;
                shopItems[choice] = (item.Name, item.Type, item.Value, item.Price, true);
                items.Add(items.Count + 1, (item.Name, item.Type, item.Value, false, true));
                Console.WriteLine("구매를 완료했습니다.");
            }
            else
            {
                Console.WriteLine("Gold 가 부족합니다.");
            }
        }
        Console.ReadKey();
    }
}
