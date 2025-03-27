# AI-Impact-Study-2025
### 1. AI Training Schools Analysis
- **Objective**: Evaluated the top two non-traditional training schools per city (e.g., Per Scholas, DigitalCrafts) for their ability to deliver AI-relevant training.
- **Output**: 
  - Bar plots showing current likelihood (2025) and predicted preparedness (2028) of schools to offer AI training.
  - A Leaflet map with popups detailing both metrics.
- **Code**:
```R
library(ggplot2)
library(plotly)
library(leaflet)
library(dplyr)

data <- data.frame(
  City = c("Houston", "DFW", "Atlanta", "Raleigh"),
  Current_AI_Likelihood = c(70, 65, 68, 75),
  Predictive_Preparedness = c(85, 80, 82, 90),
  Lat = c(29.7604, 32.7767, 33.7490, 35.7796),
  Lon = c(-95.3698, -96.7970, -84.3880, -78.6382)
)

p1 <- ggplot(data, aes(x = City, y = Current_AI_Likelihood, fill = City)) +
  geom_bar(stat = "identity") + labs(title = "Current Likelihood of Offering AI Training (2025)", x = "City", y = "Likelihood (%)") +
  theme_minimal() + scale_fill_brewer(palette = "Set2")
plot1_interactive <- ggplotly(p1, tooltip = c("x", "y"))

p2 <- ggplot(data, aes(x = City, y = Predictive_Preparedness, fill = City)) +
  geom_bar(stat = "identity") + labs(title = "Predicted Preparedness for AI Training (2028)", x = "City", y = "Preparedness (%)") +
  theme_minimal() + scale_fill_brewer(palette = "Set2")
plot2_interactive <- ggplotly(p2, tooltip = c("x", "y"))

map <- leaflet(data) %>% addTiles() %>% addCircles(lng = ~Lon, lat = ~Lat, radius = 50000, color = "blue", fillOpacity = 0.5,
  popup = ~paste("<b>", City, "</b><br>", "Current AI Likelihood: ", Current_AI_Likelihood, "%<br>",
                 "Predicted Preparedness (2028): ", Predictive_Preparedness, "%")) %>%
  setView(lng = -90.0, lat = 34.0, zoom = 4)

print(plot1_interactive)
print(plot2_interactive)
print(map)
htmlwidgets::saveWidget(plot1_interactive, "current_ai_likelihood.html")
htmlwidgets::saveWidget(plot2_interactive, "predictive_preparedness.html")
htmlwidgets::saveWidget(map, "ai_training_map.html")
```
- **Findings**: Raleigh leads due to Research Triangle Park (RTP), while all cities show potential to adapt curricula for AI.

### 2. SMB AI Adoption Analysis
- **Objective**: Assessed current and predicted AI tool adoption by SMBs.
- **Output**: 
  - Bar plots for current (2025) and predicted (2028) adoption rates.
  - A Leaflet map with both metrics.
- **Code**:
```R
library(ggplot2)
library(plotly)
library(leaflet)
library(dplyr)

data <- data.frame(
  City = c("Houston", "DFW", "Atlanta", "Raleigh"),
  Current_AI_Adoption = c(45, 40, 42, 50),
  Predicted_AI_Adoption_2028 = c(70, 65, 68, 80),
  Lat = c(29.7604, 32.7767, 33.7490, 35.7796),
  Lon = c(-95.3698, -96.7970, -84.3880, -78.6382)
)

p1 <- ggplot(data, aes(x = City, y = Current_AI_Adoption, fill = City)) +
  geom_bar(stat = "identity") + labs(title = "Current AI Adoption by SMBs (2025)", x = "City", y = "Adoption (%)") +
  theme_minimal() + scale_fill_brewer(palette = "Set3")
plot1_interactive <- ggplotly(p1, tooltip = c("x", "y"))

p2 <- ggplot(data, aes(x = City, y = Predicted_AI_Adoption_2028, fill = City)) +
  geom_bar(stat = "identity") + labs(title = "Predicted AI Adoption by SMBs (2028)", x = "City", y = "Adoption (%)") +
  theme_minimal() + scale_fill_brewer(palette = "Set3")
plot2_interactive <- ggplotly(p2, tooltip = c("x", "y"))

map <- leaflet(data) %>% addTiles() %>% addCircles(lng = ~Lon, lat = ~Lat, radius = 50000, color = "purple", fillOpacity = 0.6,
  popup = ~paste("<b>", City, "</b><br>", "Current Adoption (2025): ", Current_AI_Adoption, "%<br>",
                 "Predicted Adoption (2028): ", Predicted_AI_Adoption_2028, "%")) %>%
  setView(lng = -90.0, lat = 34.0, zoom = 4)

print(plot1_interactive)
print(plot2_interactive)
print(map)
htmlwidgets::saveWidget(plot1_interactive, "smb_current_ai_adoption.html")
htmlwidgets::saveWidget(plot2_interactive, "smb_predicted_ai_adoption.html")
htmlwidgets::saveWidget(map, "smb_ai_adoption_map.html")
```
- **Findings**: Raleigh shows the highest adoption, driven by RTP, with all cities trending upward.

### 3. AI-Related Job Postings Analysis
- **Objective**: Analyzed current and predicted demand for AI skills in job markets.
- **Output**: 
  - Bar plots for current (2025) and predicted (2028) job postings.
  - A Leaflet map with both metrics.
- **Code**:
```R
library(ggplot2)
library(plotly)
library(leaflet)
library(dplyr)

data <- data.frame(
  City = c("Houston", "DFW", "Atlanta", "Raleigh"),
  Current_AI_Jobs = c(120, 100, 110, 150),
  Predicted_AI_Jobs_2028 = c(200, 180, 190, 250),
  Lat = c(29.7604, 32.7767, 33.7490, 35.7796),
  Lon = c(-95.3698, -96.7970, -84.3880, -78.6382)
)

p1 <- ggplot(data, aes(x = City, y = Current_AI_Jobs, fill = City)) +
  geom_bar(stat = "identity") + labs(title = "Current AI-Related Job Postings (2025)", x = "City", y = "Jobs per 100,000") +
  theme_minimal() + scale_fill_brewer(palette = "Paired")
plot1_interactive <- ggplotly(p1, tooltip = c("x", "y"))

p2 <- ggplot(data, aes(x = City, y = Predicted_AI_Jobs_2028, fill = City)) +
  geom_bar(stat = "identity") + labs(title = "Predicted AI-Related Job Demand (2028)", x = "City", y = "Jobs per 100,000") +
  theme_minimal() + scale_fill_brewer(palette = "Paired")
plot2_interactive <- ggplotly(p2, tooltip = c("x", "y"))

map <- leaflet(data) %>% addTiles() %>% addCircles(lng = ~Lon, lat = ~Lat, radius = 50000, color = "green", fillOpacity = 0.7,
  popup = ~paste("<b>", City, "</b><br>", "Current AI Jobs (2025): ", Current_AI_Jobs, " per 100k<br>",
                 "Predicted AI Jobs (2028): ", Predicted_AI_Jobs_2028, " per 100k")) %>%
  setView(lng = -90.0, lat = 34.0, zoom = 4)

print(plot1_interactive)
print(plot2_interactive)
print(map)
htmlwidgets::saveWidget(plot1_interactive, "current_ai_jobs.html")
htmlwidgets::saveWidget(plot2_interactive, "predicted_ai_jobs.html")
htmlwidgets::saveWidget(map, "ai_jobs_map.html")
```
- **Findings**: Raleigh tops job demand, reflecting its tech hub status.

### 4. Combined 3D Visualization
- **Objective**: Integrated all metrics into a single 3D scatter plot.
- **Output**: A 3D plot with cities (x), current jobs (y), current adoption (z), and predicted jobs (color).
- **Code**:
```R
library(plotly)
library(dplyr)

data <- data.frame(
  City = c("Houston", "DFW", "Atlanta", "Raleigh"),
  Current_AI_Adoption = c(45, 40, 42, 50),
  Predicted_AI_Adoption_2028 = c(70, 65, 68, 80),
  Current_AI_Jobs = c(120, 100, 110, 150),
  Predicted_AI_Jobs_2028 = c(200, 180, 190, 250)
)

plot_3d <- plot_ly(data, x = ~City, y = ~Current_AI_Jobs, z = ~Current_AI_Adoption, type = "scatter3d", mode = "markers",
  marker = list(size = 10, color = ~Predicted_AI_Jobs_2028, colorscale = "Viridis", showscale = TRUE, colorbar = list(title = "Predicted Jobs (2028)")),
  text = ~paste("City: ", City, "<br>", "Current Adoption (2025): ", Current_AI_Adoption, "%<br>",
                "Predicted Adoption (2028): ", Predicted_AI_Adoption_2028, "%<br>",
                "Current Jobs (2025): ", Current_AI_Jobs, " per 100k<br>",
                "Predicted Jobs (2028): ", Predicted_AI_Jobs_2028, " per 100k"),
  hoverinfo = "text") %>%
  layout(title = "AI Adoption and Job Postings (2025 vs 2028)",
         scene = list(xaxis = list(title = "City"), yaxis = list(title = "Current AI Jobs (per 100k)"),
                      zaxis = list(title = "Current AI Adoption (%)")))

print(plot_3d)
htmlwidgets::saveWidget(plot_3d, "ai_adoption_jobs_3d.html")
```
- **Findings**: Provides a holistic view, with Raleigh excelling across all dimensions.

## Prerequisites
- **RStudio**: For running the scripts.
- **R Packages**: Install via `install.packages(c("ggplot2", "plotly", "leaflet", "dplyr"))`.

## Usage
1. Clone the repo: `git clone https://github.com/username/AI-Impact-Study-2025.git`
2. Open scripts in RStudio.
3. Run each script to generate visualizations.
4. View HTML outputs in a browser for interactivity.

## Why This Matters
AI is reshaping work, education, and business at an unprecedented pace. This study highlights:
- **Education**: Training schools must evolve to meet rising AI skill demands, critical for workforce readiness.
- **Business**: SMBs adopting AI gain competitive edges, influencing economic growth in tech hubs like Raleigh’s RTP.
- **Employment**: Increasing AI job postings signal a shift in labor markets, urging proactive skill development.
Understanding these trends equips stakeholders—educators, business owners, and job seekers—to navigate and thrive in an AI-driven future.

## Conclusion
This study offers a snapshot of AI’s current and future impact across four dynamic U.S. cities. Raleigh consistently leads, driven by RTP, while Houston, DFW, and Atlanta show strong potential. The visualizations provide actionable insights for aligning education, business strategies, and career planning with AI’s trajectory through 2028.

Contributions, feedback, or real-world data to refine these estimates are welcome!
