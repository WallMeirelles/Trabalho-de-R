install.packages("ggplot2")
library(ggplot2)

#Dispersive - Log P x Log S
ggplot(data=eye_desease_library) + 
  geom_point(mapping = aes(x=molLogP, y = molLogS, color = TARGET)) + 
  geom_smooth(mapping = aes(x=molLogP, y = molLogS, linetype= TARGET), se = FALSE) +
  facet_wrap(~TARGET, ncol = 7)

#Histogram of mol PSA
color_scale <- c("limegreen", "gold", "red")
breaks <- c(-Inf, 90, 140, Inf)
ggplot(eye_desease_library, aes(x = molPSA, fill = cut(molPSA, breaks))) +
  geom_histogram(color="black") +
  scale_fill_manual(values = color_scale)
#Histogram of mol PSA by Target
ggplot(eye_desease_library, aes(x = molPSA, fill = TARGET)) +
  geom_histogram(color="black") +
  facet_wrap(~TARGET, ncol = 7)

#Boxplot - Mol Wheight
ggplot(eye_desease_library, aes(x = TARGET, y = molWeight, fill = TARGET)) +
  geom_boxplot() 

#Boxplot - Num of HBA e HBD
ggplot(eye_desease_library, aes(x = TARGET, y = nof_HBA, fill = TARGET)) +
  geom_boxplot() 

ggplot(eye_desease_library, aes(x = TARGET, y = nof_HBD, fill = TARGET)) +
  geom_boxplot() 
