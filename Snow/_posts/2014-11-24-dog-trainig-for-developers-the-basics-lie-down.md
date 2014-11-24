---
layout: post
title: Dog training for Developers - The basics: Lie down
series:
    name: Dog training for Developers - The basics
    current: 6
    part: Dog training for Developers - The basics
    part: Dog training for Developers - The basics: Recognize the name
    part: Dog training for Developers - The basics: Come when called
    part: Dog training for Developers - The basics: Sit
    part: Dog training for Developers - The basics: Stay
    part: Dog training for Developers - The basics: Lie down
---

This is the last post of this series and I hope now you and your dog are an awesome team!

Today I will give you the tips to the lie down command, a nice complement to the Sit command.

<!--excerpt-->
![Dog lie down](/images/dog-trainig-for-developers-the-basics-lie-down.jpg)

I hope you have liked this series. If you want to have some more tips please let me know, I would be glad to know.

And remember, be patient as always :)


    public void LieDown()
    {
        var snack = _teacher.GrabNewSnack();
        _teacher.Sit();

        Sit();
        do
        {
            //Wait until dog is sitting
        } while (!_dog.IsSitting);

        for (int i = 0; i < 5; i++)
        {
            do
            {
                //your hand to the middle of his legs
                //move your hand slowly
                _teacher.MoveHandDown();
            } while (!_dog.IsLying);

            _teacher.Say("Lie down!");
            _teacher.GiveToDog(snack);

        }
    }