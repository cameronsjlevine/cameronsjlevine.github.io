---
layout: default
title: Culling the Blood Red Forest
permalink: /cullingTheBloodRedForest/
---
<link rel="shortcut icon" type="image/x-icon" href="./images/favicon.ico">

<h1 id="titleSection"></h1>

# Culling the Blood Red Forest
![image](./images/cullingTheBloodRedForestIcon2.jpg)

<iframe src="https://itch.io/embed/1321167" height="167" width="552" frameborder="0" style="display: block; margin:auto; padding-bottom: 20px;"><a href="https://cameronlevine.itch.io/culling-the-blood-red-forest">Culling the Blood Red Forest by cameronlevine</a></iframe>

Culling the Blood Red Forest is a 3D shooter where you speed around stages killing semi-aggressive forest creatures. The ultimate goal is to beat all the bosses, and in doing so, earn new guns to use on the enemies. 

## Player Movement
<iframe width="560" height="315" src="https://www.youtube.com/embed/mU8238j0IeA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="display: block; margin: auto; padding-bottom: 20px;"></iframe>

We wanted the game to be a fast-paced arena shooter, and the solution we came up with was to make the player’s movement slightly slippery. To keep the speed going, we also decided to make the walls bouncy, which really helped to keep the player on the move. Since Unity's physics are a bit naturally floaty, it only took a little bit of tinkering around to achieve the desired effect. 

<details><summary><h3><a style="cursor: pointer;">Player Movement Snippet</a></h3></summary>
{% highlight csharp %}
void FixedUpdate()
    {
        playerX = transform.forward;
        playerRight = transform.right;

        //move the player if the "wasd" keys are pressed, using acceleration to simulate slippery physics
        if (Input.GetKey(KeyCode.W))
        {
            rb.AddForce(playerX.x * acceleration, 0, playerX.z * acceleration);
        }
        if (Input.GetKey(KeyCode.A))
        {
            rb.AddForce(-playerRight.x * acceleration, 0, -playerRight.z * acceleration);
        }
        if (Input.GetKey(KeyCode.S))
        {
            rb.AddForce(-playerX.x * acceleration, 0, -playerX.z * acceleration);
        }
        if (Input.GetKey(KeyCode.D))
        {
            rb.AddForce(playerRight.x * acceleration, 0, playerRight.z * acceleration);
        }
    }
{% endhighlight %}
</details>

## Gun Design
<iframe width="560" height="315" src="https://www.youtube.com/embed/Z0DqILvfO2U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="display: block; margin: auto; padding-bottom: 20px;"></iframe>

The guns were designed to be different in the way that each of them shoot. The pistol shoots a single small shot, the shotgun shoots a burst of pellets, the grenade launcher lobs a large grenade, and the LMG shoots three bullets at once rapidly. The slippery movement also meant that the recoil of the guns could be used to push oneself backwards, allowing the player to slow down or to move backwards outright. The recoil of the LMG is so high, in fact, that you can use it to fly around the stage, making it just as fun to use as it is uncontrollable. 

<details><summary><h3><a style="cursor: pointer;">Gun Shot Snippet</a></h3></summary>
{% highlight csharp %}

{% endhighlight %}
</details>

## Enemy AI
<iframe width="560" height="315" src="https://www.youtube.com/embed/TaFPCp-oTN8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="display: block; margin: auto; padding-bottom: 20px;"></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/QZPnPXs7XdA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="display: block; margin: auto; padding-bottom: 20px;"></iframe>

The enemies' AI is programmed to wander around while not near the player, but if the player gets close, they run away. Once the player kills the first wave of enemies, they go on the attack – enemies begin to run towards the player if they get too close. Originally they only ran away, but this made the game almost impossible to lose, so our solution was to have one round passive and the next round aggressive, which also helped to keep the gameplay more fresh.

<details><summary><h3><a style="cursor: pointer;">Enemy AI Snippet</a></h3></summary>
{% highlight csharp %}

{% endhighlight %}
</details>

<hr>

<div style="text-align: center;">
  <a href="mailto:chaotixlevine@gmail.com"><img src="/./images/mail.png" style="height: 40px; margin: auto; padding-right: 10px;"></a>
  <a href="https://www.linkedin.com/in/cameron-levine-930242214"><img src="/./images/LI-In-Bug.png" style="height: 40px;"></a>
</div>
