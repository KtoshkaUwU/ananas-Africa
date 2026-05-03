from pygame import *
from random import randint

class GameSprite(sprite.Sprite):
   def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
       sprite.Sprite.__init__(self)
       self.image = transform.scale(image.load(player_image), (size_x, size_y))
       self.speed = player_speed
       self.rect = self.image.get_rect()
       self.rect.x = player_x
       self.rect.y = player_y
   def reset(self):
       window.blit(self.image, (self.rect.x, self.rect.y))
 
 
class Player(GameSprite):
    def update_r(self):
        keys = key.get_pressed()
        if keys[K_UP] and self.rect.y > 0:
            self.rect.y -= self.speed
        if keys[K_DOWN] and self.rect.y < win_height - 150:
            self.rect.y += self.speed
    
    def update_l(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 0:
            self.rect.y -= self.speed
        if keys[K_s] and self.rect.y < wssin_height - 150:
            self.rect.y += self.speed

win_width = 600
win_height = 500
display.set_caption("Ping-pong")
window = display.set_mode((win_width, win_height))
background = transform.scale(image.load('room.jpg'), (win_width, win_height))

racket1 = Player('Femboy_flag.png',30,200,30,150,1)
racket2 = Player('Femboy_flag.png',500,200,30,150,1)
ball = GameSprite('astolfo.png',200,200,50,50,1)

font.init()
font = font.Font(None, 50)

lose1 = font.render('ПЕРВЫЙ ИГРОК ПРОИГРАЛ', True, (255, 255, 255))
lose2 = font.render('ВТОРОЙ ИГРОК ПРОИГРАЛ', True, (255,255,255))

speed_x = 1
speed_y = 1

finish = False
game = True
run = True #флаг сбрасывается кнопкой закрытия окна
while run:
    for e in event.get():
        if e.type == QUIT:
           run = False

    if finish != True:
        window.blit(background,(0,0))
        racket1.update_l()
        racket2.update_r()
        ball.rect.x += speed_x
        ball.rect.y += speed_y      
        if sprite.collide_rect(racket1, ball) or sprite.collide_rect(racket2, ball):
            speed_x *= -1
            speed_y *= 1
        if ball.rect.y > win_height - 50 or ball.rect.y < 0:
            speed_y *= -1       
        if ball.rect.x < 0:
            finish = True
            window.blit(lose1, (70,20))
            game_over = True
        if ball.rect.x > win_width-50:
            finish = True
            window.blit(lose2, (70,20))
            game_over = True   
        racket1.reset()
        racket2.reset()
        ball.reset()        
        display.update()
time.delay(50)
