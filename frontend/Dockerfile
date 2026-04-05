# ------------------------------------------------------------------------------
# 🏗️ Stage 1: Frontend Build Stage (Vite / React App)
# ------------------------------------------------------------------------------

FROM node:21 AS frontend-builder

#  Set working directory inside container
WORKDIR /app

#  Copy dependency files (for better caching)
COPY package*.json ./

# Install all dependencies
RUN npm install

#  Copy complete source code to working dir
COPY . .

# Build args declare karo
ARG VITE_API_KEY
ARG VITE_Auth_Domain
ARG VITE_PROJECT_ID
ARG VITE_STORAGE_BUCKET
ARG VITE_MESSAGING_SENDERID
ARG VITE_APPID

#  Set environment to production in this stage no dev dependencies are included
ENV NODE_ENV=production
ENV VITE_API_KEY=$VITE_API_KEY
ENV VITE_Auth_Domain=$VITE_Auth_Domain
ENV VITE_PROJECT_ID=$VITE_PROJECT_ID
ENV VITE_STORAGE_BUCKET=$VITE_STORAGE_BUCKET
ENV VITE_MESSAGING_SENDERID=$VITE_MESSAGING_SENDERID
ENV VITE_APPID=$VITE_APPID

#  Inject Backend API URL (Build-time variable)
ENV VITE_API_PATH=${VITE_API_PATH}

#  Build the frontend app (creates /dist folder)
RUN npm run build

# ------------------------------------------------------------------------------
# ✅ Output: Optimized static files inside /app/dist
# Ready to be served via Nginx or any static server
# ------------------------------------------------------------------------------s
