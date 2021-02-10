---
title: Debugowanie na platformie .NET Core w systemie Linux
description: Debuguj program .NET Core w systemie Linux przy użyciu Secure Shell (SSH) przez dołączenie do procesu. Przygotuj swoją aplikację do debugowania. Kompilowanie i wdrażanie aplikacji. Dołącz debuger.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bfd1df6d977830e5b8e332efa3d0af653d3aec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934614"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Debugowanie programu .NET Core w systemie Linux przy użyciu protokołu SSH przez dołączenie do procesu

Począwszy od programu Visual Studio 2017, można dołączać do procesów .NET Core działających na lokalnym lub zdalnym wdrożeniu systemu Linux za pośrednictwem protokołu SSH. W tym artykule opisano sposób konfigurowania debugowania i debugowania. W przypadku scenariuszy debugowania przy użyciu kontenerów platformy Docker zobacz [dołączanie do procesu działającego w kontenerze platformy Docker](../debugger/attach-to-process-running-in-docker-container.md) i w zamian artykułów [narzędzi kontenerów](../containers/edit-and-refresh.md) . Aby debugować system Linux w systemie WSL 2 z programu Visual Studio (bez dołączania do procesu), zobacz [debugowanie aplikacji .NET Core w WSL 2 z programem Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

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