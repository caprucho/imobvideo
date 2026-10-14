# Execução local — experiência do padrão aprovado

O primeiro vídeo aprovado foi produzido diretamente com FFmpeg no Windows. Não depende de uma assinatura de editor nem do HyperFrames. Reutilize o método quando adequado; não reutilize os cortes, tempos, música ou dados comerciais daquele imóvel.

## Preparação

Localize Python/Node e as dependências usando o carregador de dependências do ambiente quando disponível. Verifique FFmpeg e suas capacidades. Se não existir executável local, imageio-ffmpeg pode fornecer um binário; instalar dependências de trabalho em work/ evita depender de um cache antigo. Não presuma que o comando python do Windows seja um interpretador funcional. Descubra as ferramentas em cada ambiente; não fixe caminhos de uma sessão.

Inspecione codec, resolução, FPS, rotação e duração. Um arquivo pode anunciar 1920 × 1080 com matriz de rotação e ser visualmente vertical 1080 × 1920. Honre a rotação ao gerar miniaturas, detectar movimento e renderizar. A fonte aprovada tinha 24 FPS e não era 4K.

## Seleção e estabilização

Gere folhas de contato com tempos para localizar os ambientes e reveja os trechos em movimento. Faça seleção específica para o novo imóvel; não use seleção automática sem revisão.

O método que funcionou foi vidstabdetect seguido de vidstabtransform em cada tomada, usando os mesmos tempos e orientação nas duas passagens. O recorte ficou em torno de 3,3% na primeira edição. Isso é um resultado de referência, não uma exigência universal ou garantia.

Como ponto de partida, foram usados shakiness=7, accuracy=12, smoothing=15, optalgo=gauss, optzoom=1 e interpol=bicubic. Os limites de deslocamento e rotação devem corresponder à fonte: maxshift=18 e maxangle=0.008 funcionaram naquela gravação, mas podem deixar tremores de outras fontes sem correção. Não aplicar cegamente. Verifique bordas, estabilidade e perda de enquadramento antes de generalizar parâmetros.

Em câmera lenta de 80% a 24 FPS foi usada interpolação de movimento. É uma etapa mais lenta e requer revisão visual, especialmente em linhas verticais e transições. Não confunda renderização lenta com falha; acompanhe progresso. Um recorte selecionado não pode referenciar um arquivo de movimento de outra tomada.

## Marca e composição

Use assets/s6-logo-oficial.png, que já tem transparência; não remova o fundo nem redesenhe a marca. Redimensione proporcionalmente e multiplique o canal alpha por 0,10 para a marca central com largura equivalente a 40% do vídeo. Aplique sobre toda a sequência dos ambientes para manter continuidade.

As cartelas são composições com a logo integral e fontes incluídas. Faça os fades da imagem toda. Na miniatura, duas fotos verticais podem ocupar a parte direita, com marca e chamada curta em painel grafite à esquerda. As palavras da miniatura não alteram o título do anúncio no YouTube; o sufixo opcional S6Imoveis pode ser acrescentado quando couber.

A fonte Instrument Sans tem licença OFL incluída em assets/InstrumentSans-OFL.txt. O ícone do WhatsApp foi obtido da representação oficial preservada em https://commons.wikimedia.org/wiki/File:WhatsApp.svg, com PNG de https://thumb.wikimedia.org/wikipedia/commons/thumb/6/6b/WhatsApp.svg/250px-WhatsApp.svg.png. Use-o apenas para identificar o contato no WhatsApp, preservando suas proporções.

## Montagem e conferência

Normalize resolução, FPS, SAR e formato de pixels antes de concatenar cenas. Use yuv420p, H.264 de boa qualidade e AAC; faststart facilita reprodução. Evite múltiplas recompressões desnecessárias.

Mapeie explicitamente a imagem editada e a música externa. Nunca preserve por acidente o áudio do celular. Um ponto de partida de volume é cerca de -20 LUFS, com pico verdadeiro abaixo de -2 dBTP, ajustado pelo resultado. Depois desse equilíbrio, aplique volume=0.5 para cumprir o padrão de música 50% mais baixa; se usar -20 LUFS como referência, a saída ficará aproximadamente em -26 LUFS. Não renormalize depois. Nas revisões, reduza a música da versão de referência a 50% e preserve o restante. Faça fade-in e fade-out. Não fixe os tempos de áudio antes de conhecer a duração final da montagem.

Além de decodificar o MP4 inteiro para verificar corrupção, confira imagens em todos os ambientes, limites dos cortes e as cartelas. A revisão do primeiro trabalho identificou um reflexo de quem filmava no espelho; foi retirado escolhendo um trecho posterior do mesmo banheiro, sem apagar objetos nem alterar o imóvel. Revise em detalhe regiões de espelhos, movimentos interpolados e linhas estruturais.

Não confunda validação técnica com avaliação visual: ausência de erros de codec não prova que a estabilização e os cortes ficaram bons. Abra o resultado para revisão quando o ambiente permitir e forneça links absolutos dos arquivos finais.

Nas legendas, confira se a fonte contém os glifos usados, especialmente m², acentos e R$. Caso falte o ², componha um 2 menor em sobrescrito ou use uma fonte compatível; não exporte o caractere como um quadrado vazio. Garanta a cadência de saída ao combinar overlays animados, preservando o FPS da montagem.
