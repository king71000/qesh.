name: Pull Request Build

on:

  pull_request:

    branches: 

    - dev

    - master

jobs:

  build:

    runs-on: ubuntu-latest

    steps:

    - uses: actions/checkout@v2

      

    - name: Setup .NET Core

      uses: actions/setup-dotnet@v1

      with:

        dotnet-version: 6.0.101

    

    - name: Install dependencies

      run: dotnet restore ./src/CassinoGames.sln

    

    - name: Build

      run: dotnet build ./src/CassinoGames.sln --configuration Release --no-restore

    

    - name: Test

      run: dotnet test ./src/CassinoGames.sln --configuration Release --no-build --verbosity normalرا
