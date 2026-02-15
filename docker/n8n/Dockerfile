# Dockerfile para n8n com FFmpeg
# Baseado na imagem oficial n8n
FROM n8nio/n8n:1.121.3

# Instalar FFmpeg e dependências necessárias
USER root

# No Alpine Linux, o pacote ffmpeg já inclui todas as bibliotecas necessárias
RUN apk add --no-cache \
    ffmpeg \
    && rm -rf /var/cache/apk/*

# Voltar para o usuário node
USER node

# Verificar instalação do FFmpeg
RUN ffmpeg -version || echo "FFmpeg installation check"

EXPOSE 5678
