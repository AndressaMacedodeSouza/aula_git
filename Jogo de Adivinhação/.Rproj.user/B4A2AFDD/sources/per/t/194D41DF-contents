library(shiny)

# Definir a UI
ui <- fluidPage(
  titlePanel("Jogo de Adivinhação"),
  sidebarLayout(
    sidebarPanel(
    textInput("gues", "Digite sua estimativa"),
    actionButton("submit","Enviar Palpite"),
    verbatimTextOutput("result")
    ),
    mainPanel(
      h3("Instruções"),
      p("Tende Adivinhar o número secreto!")
    )
    )
  )

# Definir o Servidor

server <- function(input, output) {
  numbersecret <- round(runif(1, 1, 100))
  observeEvent(input$submit,{
    gues <- as.numeric(input$gues)
    if (!is.na(gues)){
      if(gues == numbersecret){
        output$result <- renderText( "Parabéns! Você acertou!")
      }else if (gues < numbersecret) {
        output$result <- renderText("Tente um número maior")
      } else { 
        output$result <- renderText(" Tente um número menor.")
      }
      } else {
        output$result <- renderText(" Tente um número válido")
      }
      
  })
}

shinyApp(ui,server)
