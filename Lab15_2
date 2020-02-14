using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;

namespace Kpyap10
{
    class Program
    {
        interface IShowInfo
        {
            void ShowInfo();
        }


        public abstract class Undead
        {
            delegate void FlexHandler(string message);
            event FlexHandler Notify;

            public string Name { get; }
            public string Gender { get; }
            public int? Age { get; }
            protected int Force;
            protected int Dodge;
            protected int Exp;
            protected int Level;
            public string specialSkill;
            public List<string> Friends = new List<string>();
            protected int Money { get; set; }

            public int GetForce()
            {
                return this.Force;
            }
            public int GetLevel()
            {
                return this.Level;
            }
            void KilledMonster(int LvlMonster, string TypeMonster)
            {
                this.Money += LvlMonster / this.Level * (TypeMonster == "Human" ? 12 : 6);
                this.Exp += LvlMonster / this.Level * (TypeMonster == "Human" ? Convert.ToInt32(new Random().Next(30, 50)) : Convert.ToInt32(new Random().Next(5, 15)));
                CheckLvl();
            }
            void CheckLvl()
            {
                if (this.Exp > 1000)
                {
                    this.Level += 1;
                    this.Exp = this.Exp - 1000;
                }
            }


            void ReadThomeOfKnowlage(string NameOfSkill, int force)
            {
                Notify.Invoke("Readed!");
                this.specialSkill = NameOfSkill;
                this.Force += force;
            }

            delegate void AddFriendList(string name);
            public void AddFriend(string name)
            {
                AddFriendList Flex = Friends.Add;
                Flex(name);
            }

            void RemoveFriend(string name)
            {
                this.Friends.Remove(name);
            }

            public int GetDodge()
            {
                return this.Dodge;
            }

            private static void DisplayMessage(string message)
            {
                Console.WriteLine(message);
            }
            delegate void FlexDodgeForce();
            FlexDodgeForce FlexDelegate;    
            public Undead(string name, string gender, int age)
            {
                Notify += DisplayMessage;
                Notify.Invoke($"Created");
                this.Level = 1;
                this.Name = name;
                this.Age = age;
                this.Gender = gender;
                FlexDelegate += SetDodge;
                FlexDelegate += SetForce;
                FlexDelegate();
            }

            public void SetDodge()
            {
                Dodge = Convert.ToInt32(new Random().Next(1, 99));
            }

            public void SetForce()
            {
                Force = Convert.ToInt32(new Random().Next(1, 49));
            }
            public Undead(string name, string gender)
            {
                Notify += DisplayMessage;
                Notify.Invoke($"Created");
                this.Level = 1;
                this.Name = name;
                this.Gender = gender;
                FlexDelegate += SetDodge;
                FlexDelegate += SetForce;
                FlexDelegate();
            }

            public Undead(string name, int age)
            {
                Notify += DisplayMessage;
                Notify.Invoke($"Created");
                this.Level = 1;
                this.Name = name;
                this.Age = age;
                FlexDelegate += SetDodge;
                FlexDelegate += SetForce;
                FlexDelegate();
            }
            Undead(string name)
            {
                this.Level = 1;
                this.Name = name;
                FlexDelegate += SetDodge;
                FlexDelegate += SetForce;
                FlexDelegate();
            }
        }

       

        class UndeadHuman : Undead, IShowInfo
        {
            string StartLocation;
            int QuestIndex;
            public UndeadHuman(string name, string gender, int age) : base(name, gender, age)
            {
                SetLocation();
                this.QuestIndex = 01;
                spawn();
                Welcome();
            }

            public UndeadHuman(string name, string gender) : base(name, gender)
            {
                SetLocation();
                spawn();
                this.QuestIndex = 01;
                Welcome();
            }

            public void ShowInfo()
            {
                Console.WriteLine(this.Name);
            }

            public virtual void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} отдал честь.");
            }

            public virtual void DonateLvlUp()
            {

                base.Level += 1;
                Console.WriteLine("Cheer. Ты внес в казну золота на еще один уровень.");
            }

            protected void spawn()
            {
                Console.WriteLine($"Ваш персонаж заспавнился в локации {this.StartLocation}");
            }

            protected void Welcome()
            {
                Console.WriteLine($"Добро пожаловать в {this.StartLocation}. Возьмите ваш первый квест в таверне!");
            }
            protected virtual void SetLocation()
            {
                var rand = Convert.ToInt32(new Random().Next(1, 3));
                switch (rand)
                {
                    case 1:
                        this.StartLocation = "Леса Лордерона";
                        break;
                    case 2:
                        this.StartLocation = "Громовой Утес";
                        break;
                    case 3:
                        this.StartLocation = "Оргримар";
                        break;
                }
            }
        }

        class UndeadAnimal : Undead, IShowInfo
        {
            protected string StartLocation;
            int Height;
            string RaceSkill;
            public UndeadAnimal(string name, int height, string gender, int age) : base(name, gender, age)
            {
                this.Height = height;
                SetLocation();
                spawn();
                Welcome();
                this.RaceSkill = "Охота";
            }

            public UndeadAnimal(string name, int height, string gender) : base(name, gender)
            {
                this.Height = height;
                SetLocation();
                spawn();
                Welcome();
                this.RaceSkill = "Охота";
            }

            public void DonateLvlUp()
            {
                base.Level += 1;
                Console.WriteLine("Cheer. Ты задонатил на один уровень!");
            }

            public virtual void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} скорчил рожу.");
            }

            protected void spawn()
            {
                Console.WriteLine($"Ваш персонаж воскрес в локации {this.StartLocation}");
            }

            protected void Welcome()
            {
                Console.WriteLine($"Тебя восресили в локации {this.StartLocation}. Возьмите ваш первый квест у ближайшего чумного доктора!");
            }
            public virtual void SetLocation()
            {
                var rand = Convert.ToInt32(new Random().Next(1, 3));
                switch (rand)
                {
                    case 1:
                        this.StartLocation = "Наксрамас";
                        break;
                    case 2:
                        this.StartLocation = "Кельталас";
                        break;
                    case 3:
                        this.StartLocation = "Забытые земли";
                        break;
                }
            }

            public void ShowInfo()
            {
                Console.WriteLine(this.Name);
            }
        }

        class UndeadDoctor : UndeadHuman
        {
            string HeroClass;
            public UndeadDoctor(string name, string gender, int age) : base(name, gender, age)
            {
                this.HeroClass = "Doctor";

            }

            public UndeadDoctor(string name, int height, string gender) : base(name, gender)
            {
                this.HeroClass = "Doctor";

            }

            public override void DonateLvlUp()
            {
                base.Level += 1;
                Console.WriteLine("Cheer. Теперь ты можешь лечить еще лучше");
            }

            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} показал палец свой костлявой рукой.");
            }
        }

        class UndeadTank : UndeadAnimal
        {
            string HeroClass;
            public UndeadTank(string name, int height, string gender, int age) : base(name, height, gender, age)
            {
                this.HeroClass = "Tank";

            }

            public UndeadTank(string name, int height, string gender) : base(name, height, gender)
            {
                this.HeroClass = "Tank";

            }


            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} постучал по щиту");
            }
        }

        class UndeadLich : UndeadAnimal
        {
            string HeroClass;
            public UndeadLich(string name, int height, string gender, int age) : base(name, height, gender, age)
            {
                this.HeroClass = "Lich";

            }

            public UndeadLich(string name, int height, string gender) : base(name, height, gender)
            {
                this.HeroClass = "Lich";

            }

            public override void SetLocation()
            {
                base.StartLocation = "Цитадель Ледяной Короны";
            }
            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} воскресил ближайших трупов");
            }
        }

        class UndeadNecro : UndeadHuman
        {
            string HeroClass;
            public UndeadNecro(string name, string gender, int age) : base(name, gender, age)
            {
                this.HeroClass = "Necro";

            }

            public UndeadNecro(string name, string gender) : base(name, gender)
            {
                this.HeroClass = "Necro";

            }

            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} некротически вздохнул");
            }
        }

        class UndeadRetard : UndeadAnimal
        {
            string HeroClass;
            public UndeadRetard(string name, int height, string gender, int age) : base(name, height, gender, age)
            {
                this.HeroClass = "Retard";

            }

            public UndeadRetard(string name, int height, string gender) : base(name, height, gender)
            {
                this.HeroClass = "Retard";

            }

            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} затупил");
            }
        }

        class UndeadGnoos : UndeadHuman
        {
            string HeroClass;
            public UndeadGnoos(string name, string gender, int age) : base(name, gender, age)
            {
                this.HeroClass = "Gnoos";

            }

            public UndeadGnoos(string name, int height, string gender) : base(name, gender)
            {
                this.HeroClass = "Gnoos";

            }

            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} изверг непонятную слизь");
            }
        }

        class UndeadAssasin : UndeadAnimal
        {
            string HeroClass;
            public UndeadAssasin(string name, int height, string gender, int age) : base(name, height, gender, age)
            {
                this.HeroClass = "Tank";

            }

            public UndeadAssasin(string name, int height, string gender) : base(name, height, gender)
            {
                this.HeroClass = "Tank";

            }

            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} скрылся в тени");
            }
        }

        class UndeadBard : UndeadHuman
        {
            string HeroClass;
            public UndeadBard(string name, string gender, int age) : base(name, gender, age)
            {
                this.HeroClass = "Bard";

            }

            public UndeadBard(string name, string gender) : base(name, gender)
            {
                this.HeroClass = "Bard";

            }

            public override void Emoji()
            {
                Console.WriteLine($"Хе-хе, {base.Name} поиграл на лютне");
            }
        }

        static void PrintHeroes(ArrayList Heroes)
        {
            foreach (var h in Heroes)
            {
                object type = h.GetType();
                switch (type.ToString())
                {
                    case "Kpyap10.Program+UndeadAnimal":
                        var f = (UndeadAnimal)h;
                        Console.WriteLine("Name: " + f.Name + "\tAge: " + f.Age + "\tLevel: " + f.GetLevel() + "\tForce" + f.GetForce());
                        break;
                    case "Kpyap10.Program+UndeadDoctor":
                        var d = (UndeadDoctor)h;
                        Console.WriteLine("Name: " + d.Name + "\tAge: " + d.Age + "\tLevel: " + d.GetLevel() + "\tForce" + d.GetForce());
                        break;

                    case "Kpyap10.Program+UndeadTank":
                        var t = (UndeadTank)h;
                        Console.WriteLine("Name: " + t.Name + "\tAge: " + t.Age + "\tLevel: " + t.GetLevel() + "\tForce" + t.GetForce());
                        break;
                    case "Kpyap10.Program+UndeadAssasin":
                        var a = (UndeadAssasin)h;
                        Console.WriteLine("Name: " + a.Name + "\tAge: " + a.Age + "\tLevel: " + a.GetLevel() + "\tForce" + a.GetForce());
                        break;
                    case "Kpyap10.Program+UndeadBard":
                        var b = (UndeadBard)h;
                        Console.WriteLine("Name: " + b.Name + "\tAge: " + b.Age + "\tLevel: " + b.GetLevel() + "\tForce" + b.GetForce());
                        break;
                    case "Kpyap10.Program+UndeadGnoos":
                        var g = (UndeadGnoos)h;
                        Console.WriteLine("Name: " + g.Name + "\tAge: " + g.Age + "\tLevel: " + g.GetLevel() + "\tForce" + g.GetForce());
                        break;
                    case "Kpyap10.Program+UndeadNecro":
                        var n = (UndeadNecro)h;
                        Console.WriteLine("Name: " + n.Name + "\tAge: " + n.Age + "\tLevel: " + n.GetLevel());
                        break;
                    case "Kpyap10.Program+UndeadHuman":
                        var r = (UndeadHuman)h;
                        Console.WriteLine("Name: " + r.Name + "\tAge: " + r.Age + "\tLevel: " + r.GetLevel());
                        break;
                    case "Kpyap10.Program+UndeadLich":
                        var l = (UndeadAnimal)h;
                        Console.WriteLine("Name: " + l.Name + "\tAge: " + l.Age + "\tLevel: " + l.GetLevel());
                        break;
                    case "Kpyap10.Program+Undead":
                        var u = (Undead)h;
                        Console.WriteLine("Name: " + u.Name + "\tAge: " + u.Age + "\tLevel: " + u.GetLevel());
                        break;
                    case "Kpyap10.Program+UndeadRetard":
                        var re = (UndeadRetard)h;
                        Console.WriteLine("Name: " + re.Name + "\tAge: " + re.Age + "\tLevel: " + re.GetLevel());
                        break;


                }

            }
        }

        static List<Undead> SortHeroes(List<Undead> Heroes)
        {
            Console.WriteLine("What u want?\n1.Sort by Level.\n2.Sort by Name.\n3.Sort by Force.\n4.Sort by Dodge\n5.Sort By Age.");
        Flex:
            IOrderedEnumerable<Undead> sortedUsers;
            try
            {
                switch (Convert.ToInt32(Console.ReadLine()))
                {
                    case 1:
                        sortedUsers = Heroes.OrderBy(u => u.GetLevel());
                        Console.WriteLine($"Minimal: {sortedUsers.Min(i => i.GetLevel())}, Maximal {sortedUsers.Max(i => i.GetLevel())}");
                        break;
                    case 2:
                        sortedUsers = Heroes.OrderBy(u => u.Name);
                        break;
                    case 3:
                        sortedUsers = Heroes.OrderBy(u => u.GetForce());
                        Console.WriteLine($"Minimal: {sortedUsers.Min(i => i.GetForce())}, Maximal {sortedUsers.Max(i => i.GetForce())}");
                        break;
                    case 4:
                        sortedUsers = Heroes.OrderBy(u => u.GetDodge());
                        Console.WriteLine($"Minimal: {sortedUsers.Min(i => i.GetDodge())}, Maximal {sortedUsers.Max(i => i.GetDodge())}");
                        break;
                    case 5:
                        sortedUsers = Heroes.OrderBy(u => u.Age);
                        Console.WriteLine($"Minimal: {sortedUsers.Min(i => i.Age)}, Maximal {sortedUsers.Max(i => i.Age)}");
                        break;
                    default:
                        Console.WriteLine("Bad.");
                        goto Flex;
                }
                return sortedUsers.ToList();
            }
            catch (FormatException)
            {
                Console.WriteLine("Bad");
                goto Flex;
            }
        }



        static void Main(string[] args)
        {

            ArrayList Heroes = new ArrayList();



            var AnimalDead = new UndeadAnimal("Чумной1337", 84, "Man", 14);
            Heroes.Add(AnimalDead);
            AnimalDead.Emoji();
            AnimalDead.DonateLvlUp();
            AnimalDead.AddFriend("Flex");
            Console.WriteLine(AnimalDead.Friends[0]);
            Console.WriteLine($"Текущий уровень: {AnimalDead.GetLevel()}");
            Console.WriteLine();

            var UndeadDoc = new UndeadDoctor("УбийцаГоблинов", "Man", 32);
            Heroes.Add(UndeadDoc);
            UndeadDoc.Emoji();
            UndeadDoc.DonateLvlUp();
            Console.WriteLine($"Текущий уровень: {AnimalDead.GetLevel()}");
            Console.WriteLine();

            var UndeadTanks = new UndeadTank("Пендос", 42, "Woman", 32);
            Heroes.Add(UndeadTanks);
            UndeadTanks.Emoji();
            UndeadTanks.DonateLvlUp();
            Console.WriteLine();

            var Undeadassassin = new UndeadAssasin("КиллерНуб", 214, "Дикий");
            Heroes.Add(Undeadassassin);
            Undeadassassin.Emoji();
            Console.WriteLine();

            var Undeadbard = new UndeadBard("Гитарист", "Man", 12);
            Heroes.Add(Undeadbard);
            Undeadbard.Emoji();
            Console.WriteLine();

            var Undeadgnoos = new UndeadGnoos("Червяк", 20, "Пустой");
            Heroes.Add(Undeadgnoos);
            Undeadgnoos.Emoji();
            Console.WriteLine();

            var Undeadnecro = new UndeadNecro("Некролит", "Man", 215);
            Heroes.Add(Undeadnecro);
            Undeadnecro.Emoji();
            Console.WriteLine();

            var UndeadMan = new UndeadHuman("ТупаЧелик", "Man");
            Heroes.Add(UndeadMan);
            UndeadMan.Emoji();
            Console.WriteLine();

            var UndeadLich = new UndeadLich("Артас", 193, "Undead", 98);
            Heroes.Add(UndeadLich);
            UndeadLich.Emoji();
            Console.WriteLine();

            var UndeadNotLich = new UndeadRetard("Тард", 140, "Reflex");
            Heroes.Add(UndeadNotLich);
            UndeadNotLich.Emoji();
            Console.WriteLine();


            PrintHeroes(Heroes);








            Console.ReadKey();
        }
    }
}
