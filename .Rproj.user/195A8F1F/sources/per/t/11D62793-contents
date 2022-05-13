
pegar_info_fundos <- function(id){
  
  link <- "https://www.safra.com.br/safra-asset/lista-de-fundos-de-investimento.htm"
  
  Fundos <- rvest::read_html(link) %>% 
    rvest::html_element(id) %>% 
    rvest::html_elements("h2") %>% 
    rvest::html_text() %>% 
    stringr::str_squish()
  
  Tempo <- rvest::read_html(link) %>% 
    rvest::html_element(id) %>% 
    rvest::html_elements(".fundo-infos") %>% 
    rvest::html_text() %>% 
    stringr::str_squish() %>% 
    gsub( pattern = "R\\$ ", replacement = "R\\$") %>% 
    .[-1] %>% 
    stringr::word(2) %>% 
    readr::parse_number()
  
  tibble::tibble(
    Fundos, Tempo
  )
  
}

ids <- c("#class-renda-fixa", "#class-multimercados", "class-renda-variavel", "class-previdencia")

fundos_safra <- purrr::map_dfr(ids, pegar_info_fundos) 



