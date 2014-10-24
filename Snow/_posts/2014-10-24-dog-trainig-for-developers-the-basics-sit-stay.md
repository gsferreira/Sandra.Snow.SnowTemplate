---
layout: post
title: Dog training for Developers - The basics: Stay
series:
    name: Dog training for Developers - The basics
    current: 5
    part: Dog training for Developers - The basics
    part: Dog training for Developers - The basics: Recognize the name
    part: Dog training for Developers - The basics: Come when called
    part: Dog training for Developers - The basics: Sit
    part: Dog training for Developers - The basics: Stay
    part: Dog training for Developers - The basics: Lie
---

Training a dog to stay can be a tough task, because your dog is used to following you. After you and your dog have mastered the sit command, train him to stay.

<!--excerpt-->

And remember, be patient :)

![Dog insane](/images/dog-trainig-for-developers-the-basics-sit-stay.jpg)

    public void Stay()
    {
        _teacher.Say("Sit!");
        _teacher.ShowHandInStayCommand();
        _teacher.Say("Stay!");

        System.Threading.Thread.Sleep(2000); //Wait 2 seconds

        _teacher.Say("Go play!");

        _teacher.PlayWithDog(_dog);



        _teacher.Say("Sit!");
        _teacher.ShowHandInStayCommand();

        _teacher.Say("Stay!");
        _teacher.MoveAway(numberOfSteps: 1);

        System.Threading.Thread.Sleep(2000); //Wait 2 seconds

        _teacher.Say("Go play!");

        _teacher.PlayWithDog(_dog);


        for (int i = 0; i < 5; i++)
        {
            _teacher.Say("Sit!");
            _teacher.ShowHandInStayCommand();

            _teacher.Say("Stay!");
            _teacher.MoveAway(numberOfSteps: 3);

            System.Threading.Thread.Sleep(2000 + (1000 * i)); //Wait 2 seconds

            _teacher.Say("Go play!");

            _teacher.PlayWithDog(_dog);

        }
    }