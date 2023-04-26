# Automacao-shell-script
automacao linux 
#!/bin/bash

DIRDEST=$HOME/Backup

if [ ! -d $DIRDEST ]
then
        echo "Criando Diretorio $DIRDEST..."
        mkdir -p $DIRDEST
fi

DAYS1=$(find $DIRDEST -ctime -1 - name backup_home/*tgz)

if [ "SDAYS1" ]
then
        echo "Gerado Backup do diretorio $HOME no ultimo dia. "
        echo "Continuar? : (S/N). "
        read -n1 CONT
        echo 
        if [ "$CONT" = N -o "$CONT" = n -o "$CONT" = "" ]
        then
                echo "Backup nao criado!"
                exit 1
        elif [ $CONT = S -o $CONT = s ]
        then
                echo "Sera criado um novo backup."
        else
                echo "Option Invalido"
                exit 2
        fi
fi

echo "Criando um Backup..."
ARQ="back_home_$(date +%Y%m%d%H%M).tgz"
