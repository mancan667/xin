import pygame
import math

# 初始化 Pygame
pygame.init()

# 创建屏幕
size = (800, 600)
screen = pygame.display.set_mode(size)
pygame.display.set_caption("心形特效")

# 颜色设置
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# 循环，直到用户点击关闭按钮
done = False

# 创建时钟对象
clock = pygame.time.Clock()

# 主循环
while not done:
    # 检查事件队列
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            done = True

    # 清屏
    screen.fill(WHITE)

    # 画心形
    for i in range(0, 360, 5):
        angle = i * math.pi / 180
        x = int(200 * (16 * math.sin(angle) ** 3))
        y = int(200 * (13 * math.cos(angle) - 5 * math.cos(2 * angle) - 2 * math.cos(3 * angle) - math.cos(4 * angle)))
        pygame.draw.circle(screen, RED, (x + 400, y + 300), 2)

    # 更新屏幕
    pygame.display.flip()

    # 控制帧率
    clock.tick(60)

# 关闭 Pygame
pygame.quit()
