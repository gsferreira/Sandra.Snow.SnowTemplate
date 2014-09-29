---
layout: post
title: Dog training for Developers - The basics: Recognize the name
series:
    name: Dog training for Developers - The basics
    current: 2
    part: Dog training for Developers - The basics
    part: Dog training for Developers - The basics: Recognize the name
    part: Dog training for Developers - The basics: Come when called
    part: Dog training for Developers - The basics: Sit
    part: Dog training for Developers - The basics: Stay
    part: Dog training for Developers - The basics: Lie
---

The name of your dog will be the most useful command that you will have. Your dog will need some training until recognize it, so I will leave here a method (coded in c#) of how to help him to accomplish that.

<!--excerpt-->

First, pick the perfect name for your puppy, then sit down and call the following method. You should run this method twice a day until your dog recognize his name.

Be patient, the results can take some time to appear :)


    public class DogTraining
    {
        private readonly Person _teacher;
        private readonly Dog _dog;

        public DogTraining(Person teacher, Dog dog)
        {
            this._dog = dog;
            this._teacher = teacher;

        }
        public void RecognizeName(string dogName)
        {
            //Prepare yourself
            _teacher.Sit();
            var snack = _teacher.GrabNewSnack();

            //First step - Request dog attention
            do
            {
                _teacher.ShowToDog(snack);

            }while(!_dog.IsLooking);

            _teacher.Say(dogName);

            _teacher.GiveToDog(snack);

            //Second step - Repeat action
            for (int i = 0; i < 5; i++)
            {
                snack = _teacher.GrabNewSnack();
                _teacher.HideFromDog(snack);

                do
                {
                    //wait
                } while (!_dog.IsDistracted);

                do
                {
                    _teacher.ShowToDog(snack);

                } while (!_dog.IsLooking);

                _teacher.Say(dogName);

                _teacher.GiveToDog(snack);
            }


            //Third step - Test the results
            for (int i = 0; i < 3; i++)
            {
                snack = _teacher.GrabNewSnack();
                _teacher.HideFromDog(snack);

                do
                {
                    //wait
                } while (!_dog.IsDistracted);

                
                do
                {
                    _teacher.Say(dogName);

                } while (!_dog.IsLooking);

                _teacher.GiveToDog(snack);

            }

            
        }
    }