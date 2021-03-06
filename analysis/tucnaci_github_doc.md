---
title: "tucnaci"
output: github_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE, warning = FALSE, message = FALSE, fig.height=6, fig.width=8)
```

# Library
```{r}
library(palmerpenguins)
library(here)
library(ggplot2)
library(dplyr)
```

# Input 
```{r}
data <- penguins
```

# Plot by species
```{r}
ggplot(data = data, aes(x = bill_length_mm, y = bill_depth_mm, colour = species, shape = species)) +
  geom_point() +
  scale_color_manual(values = c("darkorange","purple","cyan4")) +
  theme_classic() +
  geom_smooth(method = "lm", se = FALSE)
```

# Plot all
```{r}
ggplot(data = data, aes(x = bill_length_mm, y = bill_depth_mm)) +
  geom_point() +
  scale_color_manual(values = c("darkorange","purple","cyan4")) +
  theme_classic() +
  geom_smooth(method = "lm", se = FALSE)
```

# Plot body mass and flipper length
```{r}
mass_flipper <- ggplot(data = penguins, 
                       aes(x = flipper_length_mm,
                           y = body_mass_g)) +
  geom_point(aes(color = species, 
                 shape = species),
             size = 3,
             alpha = 0.8) +
  scale_color_manual(values = c("darkorange","purple","cyan4")) +
  labs(title = "Penguin size, Palmer Station LTER",
       subtitle = "Flipper length and body mass for Adelie, Chinstrap and Gentoo Penguins",
       x = "Flipper length (mm)",
       y = "Body mass (g)",
       color = "Penguin species",
       shape = "Penguin species") +
  theme(legend.position = c(0.2, 0.7),
        plot.title.position = "plot",
        plot.caption = element_text(hjust = 0, face= "italic"),
        plot.caption.position = "plot")+
   geom_smooth(method = "lm", se = FALSE, aes(color = species))
mass_flipper
```



# Session Info
```{r}
sessionInfo()
```

