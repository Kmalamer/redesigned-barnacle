name: Instalar Windows



on: [push, pull_request]



jobs:

  install-windows:

    runs-on: windows-latest



    steps:

    - name: Verificar Repositorio

      uses: actions/checkout@v2



    - name: Configurar Variaveis do ambiente

      run: |

        echo Setting up Windows environment



    - name: Instalar Chocolatey

      run: |

        Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString( https://chocolatey.org/install.ps1 ))



    - name: Instalar Git

      run: |

        choco install git -y



    - name: Downloading & Installing Essentials

      run: |

        Invoke-WebRequest -Uri "https://www.dropbox.com/scl/fi/qdyd4p9t6xoabl95n5o3g/Downloads.bat?rlkey=snr74vv1vr8k5suujugvrhjtm&dl=1" -OutFile "Downloads.bat"

        cmd /c Downloads.bat

        

    - name: Instalar VS Code

      run: |

        choco install vscode -y

    - name: Log In To AnyDesk

      run: cmd /c show.bat



    - name: Time Counter

      run: python time.py

