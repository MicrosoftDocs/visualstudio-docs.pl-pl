---
title: Debugowanie programu .NET Core w systemie Linux
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39b77d68e7f8876f7e0d038166f4b2a6517bb3cb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671509"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Debugowanie programu .NET Core w systemie Linux przy użyciu protokołu SSH przez dołączenie do procesu

Począwszy od programu Visual Studio 2017, można dołączać do procesów .NET Core działających na lokalnym lub zdalnym wdrożeniu systemu Linux za pośrednictwem protokołu SSH. W tym artykule opisano sposób konfigurowania debugowania i debugowania. W przypadku scenariuszy debugowania przy użyciu kontenerów platformy Docker należy zapoznać [się z tematem Dołącz do procesu uruchomionego w kontenerze platformy Docker](../debugger/attach-to-process-running-in-docker-container.md) .

## <a name="prerequisites"></a>Wymagania wstępne

- Na komputerze z programem Visual Studio należy zainstalować **ASP.NET oraz obciążenie programowanie** dla **wielu platform** w sieci Web.

- Na serwerze z systemem Linux należy zainstalować serwer SSH, rozpakować i zainstalować przy użyciu opcji zwinięcie lub Wget. Na przykład w Ubuntu można to zrobić, uruchamiając polecenie:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- Na serwerze z systemem Linux [Zainstaluj środowisko uruchomieniowe .NET w systemie Linux](/dotnet/core/install/linux)i Znajdź stronę pasującą do dystrybucji systemu Linux (na przykład Ubuntu). Zestaw SDK platformy .NET nie jest wymagany.

- Aby uzyskać wyczerpujące instrukcje dotyczące ASP.NET Core, zobacz [host ASP.NET Core w systemie Linux przy użyciu Nginx](/aspnet/core/host-and-deploy/linux-nginx) i [hosta ASP.NET Core w systemie Linux z Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Przygotowywanie aplikacji do debugowania

Aby przygotować aplikację do debugowania:

- Podczas kompilowania aplikacji należy rozważyć użycie konfiguracji debugowania. Jest to znacznie trudniejsze do debugowania kodu skompilowanego w wersji detalicznej (Konfiguracja wydania) niż kod skompilowany przez program Debug. Jeśli konieczne jest użycie konfiguracji wydania, należy najpierw wyłączyć Tylko mój kod. Aby wyłączyć to ustawienie, wybierz **Narzędzia**  >  **Opcje**  >  **debugowanie**, a następnie usuń zaznaczenie opcji **Włącz tylko mój kod**.

- Upewnij się, że projekt jest skonfigurowany do tworzenia [przenośnych plików PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (jest to ustawienie domyślne) i upewnij się, że plików PDB znajdują się w tej samej lokalizacji co Biblioteka DLL. Aby skonfigurować to w programie Visual Studio, kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**  >  **Kompiluj**  >  **Zaawansowane**  >  **Informacje o debugowaniu**.

## <a name="build-and-deploy-the-application"></a>Kompilowanie i wdrażanie aplikacji

Przed debugowaniem można użyć kilku metod. Możesz na przykład:

- Skopiuj źródła na komputer docelowy i skompiluj je na komputerze z ```dotnet build``` systemem Linux.

- Skompiluj aplikację w systemie Windows, a następnie przenieś artefakty kompilacji na maszynę z systemem Linux. (Artefakty kompilacji składają się z samej aplikacji, przenośnej plików PDB, wszystkich bibliotek środowiska uruchomieniowego, od których może zależeć, a *.deps.jsw* pliku).

Po wdrożeniu aplikacji Uruchom aplikację.

## <a name="attach-the-debugger"></a>Dołącz debuger

Gdy aplikacja jest uruchomiona na komputerze z systemem Linux, można przystąpić do dołączania debugera.

1. W programie Visual Studio wybierz polecenie **Debuguj**  >  **Dołącz do procesu...**.

1. Na liście **Typ połączenia** wybierz pozycję **SSH**.

1. Zmień **miejsce docelowe połączenia** na adres IP lub nazwę hosta komputera docelowego.

   Jeśli poświadczenia nie zostały jeszcze podane, zostanie wyświetlony monit o podanie hasła i/lub pliku klucza prywatnego.

   Nie ma wymagań dotyczących portów do skonfigurowania, z wyjątkiem portu, na którym działa serwer SSH.

1. Znajdź proces, który chcesz debugować.

   Kod jest uruchamiany przy użyciu unikatowej nazwy procesu lub procesu o nazwie dotnet. Aby znaleźć interesujący Cię proces, zaznacz kolumnę **tytuł** , która pokazuje argumenty wiersza polecenia dla procesu.

   W poniższym przykładzie zostanie wyświetlona lista procesów ze zdalnego komputera z systemem Linux za pośrednictwem transportu SSH wyświetlanego w oknie dialogowym **Dołącz do procesu** .

   ![Dołącz do procesu systemu Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Wybierz **Dołącz**.

1. W wyświetlonym oknie dialogowym Wybierz typ kodu, który chcesz debugować. Wybierz pozycję **zarządzane (.NET Core dla systemu UNIX)**.

1. Debuguj aplikację przy użyciu funkcji debugowania programu Visual Studio.

   W poniższym przykładzie widać, że debuger programu Visual Studio został zatrzymany w punkcie przerwania w kodzie uruchomionym na zdalnym komputerze z systemem Linux.

   ![Trafienie punktu przerwania](media/remote-debug-linux-over-ssh-hit-breakpoint.png)