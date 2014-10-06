---
layout: post
title: Dog training for Developers - The basics: Come when called
series:
    name: Dog training for Developers - The basics
    current: 3
    part: Dog training for Developers - The basics
    part: Dog training for Developers - The basics: Recognize the name
    part: Dog training for Developers - The basics: Come when called
    part: Dog training for Developers - The basics: Sit
    part: Dog training for Developers - The basics: Stay
    part: Dog training for Developers - The basics: Lie
---

Your dog ignores when you call him? Well, you can help him understand that you would be glad if he came to you when you want.

<!--excerpt-->

Run the following method during a few days, but don't run it more than once a day.

Remember, be patient :)

    public void ComeWhenCalled()
    {
        for (int i = 0; i < 10; i++)
        {
            var snack = _teacher.GrabNewSnack();

            //Request dog attention
            do
            {
                _teacher.ShowToDog(snack);

            } while (!_dog.IsLooking);

            _teacher.GoAway(meters: 2);

            //Open arms to invite the dog
            _teacher.OpenArms();

            while (_dog.IsComming || !_dog.IsNearTeacher)
            {
                _teacher.Say("Here!");

                _teacher.ShowToDog(snack);

            }

            _teacher.GrabDogCollar(_dog);
            //To receive the snack the dog should stay near you
            _teacher.GiveToDog(snack);

        }
    }