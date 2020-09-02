---
title: Zdalne debugowanie .NET Core w systemie Linux | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "78200924"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Zdalne debugowanie .NET Core w systemie Linux przy użyciu protokołu SSH

Począwszy od programu Visual Studio 2017, można dołączyć do procesów .NET Core działających w systemie Linux za pośrednictwem protokołu SSH. W tym artykule opisano sposób konfigurowania debugowania i debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

Na komputerze z programem Visual Studio należy zainstalować **ASP.NET oraz obciążenie programowanie** dla **wielu platform** w sieci Web.

Na serwerze z systemem Linux należy zainstalować serwer SSH, rozpakować i zainstalować przy użyciu opcji zwinięcie lub Wget. Na przykład w Ubuntu można to zrobić, uruchamiając polecenie:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Kompilowanie i wdrażanie aplikacji

Aby przygotować aplikację do debugowania:

- Podczas kompilowania aplikacji należy rozważyć użycie konfiguracji debugowania. Jest to znacznie trudniejsze do debugowania kodu skompilowanego w wersji detalicznej (Konfiguracja wydania) niż kod skompilowany przez program Debug. Jeśli konieczne jest użycie konfiguracji wydania, należy najpierw wyłączyć Tylko mój kod. Aby wyłączyć to ustawienie, wybierz **Narzędzia**  >  **Opcje**  >  **debugowanie**, a następnie usuń zaznaczenie opcji **Włącz tylko mój kod**.

- Upewnij się, że projekt jest skonfigurowany do tworzenia [przenośnych plików PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (jest to ustawienie domyślne) i upewnij się, że PBDs znajdują się w tej samej lokalizacji co Biblioteka DLL. Aby skonfigurować to w programie Visual Studio, kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**  >  **Kompiluj**  >  **Zaawansowane**  >  **Informacje o debugowaniu**.

Przed debugowaniem można użyć kilku metod. Możesz na przykład:

- Skopiuj źródła na komputer docelowy i skompiluj je na komputerze z ```dotnet build``` systemem Linux.

- Skompiluj aplikację w systemie Windows i Przenieś artefakty kompilacji na maszynę z systemem Linux. (Artefakty kompilacji składają się z samej aplikacji, wszystkich bibliotek środowiska uruchomieniowego, od których może zależeć, i *.deps.jsw* pliku).

## <a name="attach-the-debugger"></a>Dołącz debuger

Po skonfigurowaniu komputerów Uruchom aplikację na komputerze z systemem Linux, a następnie przystąpić do dołączenia debugera.

1. W programie Visual Studio wybierz polecenie **Debuguj**  >  **Dołącz do procesu...**.

1. Na liście **Typ połączenia** wybierz pozycję **SSH**.

1. Zmień **miejsce docelowe połączenia** na adres IP lub nazwę hosta komputera docelowego.

1. Znajdź proces, który chcesz debugować.

   Kod jest uruchamiany przy użyciu unikatowej nazwy procesu lub procesu o nazwie dotnet. Aby znaleźć interesujący Cię proces, zaznacz kolumnę **tytuł** , która pokazuje argumenty wiersza polecenia dla procesu.

   W poniższym przykładzie zostanie wyświetlona lista procesów ze zdalnego komputera z systemem Linux za pośrednictwem transportu SSH wyświetlanego w oknie dialogowym **Dołącz do procesu** .

   ![Dołącz do procesu systemu Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Wybierz **Dołącz**.

1. W wyświetlonym oknie dialogowym Wybierz typ kodu, który chcesz debugować. Wybierz pozycję **zarządzane (.NET Core dla systemu UNIX)**.

1. Debuguj aplikację przy użyciu funkcji debugowania programu Visual Studio.

   W poniższym przykładzie widać, że debuger programu Visual Studio został zatrzymany w punkcie przerwania w kodzie uruchomionym na zdalnym komputerze z systemem Linux.

   ![Trafienie punktu przerwania](media/remote-debug-linux-over-ssh-hit-breakpoint.png)