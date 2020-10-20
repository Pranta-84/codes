install.packages("readr")
library(readr)
beer_awards <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-10-20/beer_awards.csv')

#frequency table of state
table(beer_awards$state)

#selected the top 7 winning state


#plotted the graph
beer_awards %>%
    select(state,medal) %>%
    filter(state==c("CA","CO","OR","PA","TX","WA","WY")) %>%
    ggplot(aes(x=state,fill=medal))+
    geom_bar(position = "dodge")+
    scale_fill_manual(values=c("brown","gold","dark grey" ))+
    labs(x="State",y="Count",title="Medals won by top 7 winning states")+
    theme(panel.background=element_blank(),text=element_text(family="times new roman",face='bold',size=16))
    
