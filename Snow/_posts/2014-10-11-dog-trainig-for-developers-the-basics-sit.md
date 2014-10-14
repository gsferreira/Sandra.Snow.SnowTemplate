---
layout: post
title: Dog training for Developers - The basics: Sit
series:
    name: Dog training for Developers - The basics
    current: 4
    part: Dog training for Developers - The basics
    part: Dog training for Developers - The basics: Recognize the name
    part: Dog training for Developers - The basics: Come when called
    part: Dog training for Developers - The basics: Sit
    part: Dog training for Developers - The basics: Stay
    part: Dog training for Developers - The basics: Lie
---

"Sit" is probably one of the easiest commands to teach your dog.
But, how to accomplish it? Run the following method during a few days, twice a day.

<!--excerpt-->

Remember, be patient :)

![Feijão](/images/dog-trainig-for-developers-the-basics-sit-feijao.jpg)

    public void Sit()
    {

        //Prepare yourself
        _teacher.Sit();

        for (int i = 0; i < 4; i++)
        {
            var snack = _teacher.GrabNewSnack();

            _teacher.LetDogSniff(snack);

            //Dog should follow your hand
            do
            {
                //Dog will try to reach the food
                _teacher.MoveHandUp();

            } while (!_dog.IsSeated);

            _teacher.Say("Sit!");

            _teacher.GiveToDog(snack);
        }

        for (int i = 0; i < 5; i++)
        {
            var snack = _teacher.GrabNewSnack();
            
            _teacher.Say("Sit!");

            do
            {
                _teacher.MoveHandUp();

            } while (!_dog.IsSeated);

            _teacher.GiveToDog(snack);
        }
        
        _teacher.GetUp();
        
        for(int i=0;i<3;i++)
        {
            //Leave 
            _teacher.Say("Sit!");

            do
            {
                _teacher.MoveHandUp(); //With empty hand
            } while (!_dog.IsSeated);

            _teacher.PlayWithDog(_dog);

        }

    }