# shooter_python
убийство богов
Это игра под названием  "Shooter_game". Это очень интересная игра!
В этой игре мы играем за космический корабль и наша задача: не дать инопланетянинам косеутся края экрана!
Звучит легко, сделать тоже!С самого начала мы  ипортируем подуль PyGame.
Потом создаем классы. Самый главный класс - GameSprite. Он отец всех классов
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
Потом создаем классы игрока и врагов
class Player(GameSprite):
   def update(self):
       keys = key.get_pressed()
       if keys[K_a] and self.rect.x > 5:
           self.rect.x -= self.speed
       if keys[K_d] and self.rect.x < win_width - 80:
           self.rect.x += self.speed
   def fire(self):
       bullet = Bullet(img_bullet, self.rect.centerx, self.rect.top, 15, 20, -50)
       bullets.add(bullet)

class Enemy(GameSprite):
  def update(self):
      self.rect.y += self.speed
      global lost
      if self.rect.y > win_height:
          self.rect.x = randint(80, win_width - 80)
          self.rect.y = 0
          lost = lost + 1
 создаем главный цикл while - благодаря ему у нас будет работать все. 
 в этом цикле прописываем update; reset; нажатие на клавиши; счет и так далее
 Игра получилась хорошая, но я решил добвить несколько читов...
 На цифру 1 : мнгновенная победа
На цифру 2: + 1 жизнь
На цифру 3: + 6 врага
На цифру 4: + 1000 патронов
 Игра готова! Можно играть!
