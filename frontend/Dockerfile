# Step 1: Use the official Node.js 14.21.3 image as the build environment
FROM node:14.21.3 AS build

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy package.json and package-lock.json for dependency installation
COPY package.json package-lock.json ./

# Step 4: Install dependencies
RUN npm install

# Step 5: Copy the rest of the application files
COPY . .

# Step 6: Expose the React development server port
EXPOSE 3000

# Step 7: Start the React development server
CMD ["npm", "start", "--", "--host=0.0.0.0", "--port=3000"]


