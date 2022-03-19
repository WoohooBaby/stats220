# This is the markdown file


```{r}
library(magick)
angry_cat <- image_read('https://pic2.zhimg.com/80/v2-8742aacd3924757631da263206d48665_1440w.jpg') %>%
              image_scale(500)
crying_cat <- image_read('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTrgrYRWlXGbKItseR1hKUockMEENDsT2BZeA&usqp=CAU') %>%
              image_scale(500)

text_1 <- image_blank(width = 500, height = 425, color = 'white') %>%
          image_annotate(text = 'When i was arguing\nwith my mom', size = 50, font = "Impact", gravity = 'center')

text_2 <- image_blank(width = 500, height = 516, color = 'white') %>%
          image_annotate(text = 'When mom ask me to\nhave dinner', size = 50, font = "Impact", gravity = 'center')

angry_cat_new <- angry_cat %>%
                 image_annotate(text = 'I will never\ntalk with you\nanymore !', size = 40, color = 'white', font = "Impact", gravity = 'south')

crying_cat_new <- crying_cat %>%
                 image_annotate(text = 'Still me\n', size = 40, color = 'white', font = "Impact", gravity = 'south')

img_pack <- c(text_1, text_2, angry_cat_new, crying_cat_new)

first_row <- c(text_1, angry_cat_new) %>%
              image_append()
second_row <- c(text_2, crying_cat_new) %>%
              image_append()

meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE)

image_write(meme, '220meme.png')

```
