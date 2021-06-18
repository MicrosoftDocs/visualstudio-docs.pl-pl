---
title: Instalowanie certyfikatów dla instalacji w trybie offline
description: Dowiedz się, jak zainstalować certyfikaty dla aplikacji Visual Studio w trybie offline.
ms.date: 03/29/2021
ms.custom: seodec18, SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6dc4137157e2fa5136a0b8c86c5cf72f284a9eb7
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307379"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Instalowanie certyfikatów wymaganych do instalacji Visual Studio offline

Visual Studio jest przeznaczony głównie do instalowania na komputerze połączonym z Internetem, ponieważ wiele składników jest regularnie aktualizowanych. Jednak w przypadku niektórych dodatkowych kroków można wdrożyć usługę Visual Studio w środowisku, w którym działa połączenie internetowe jest niedostępne.

Aparat Visual Studio instaluje tylko zaufaną zawartość. W tym celu sprawdza podpisy authenticode pobieranej zawartości i sprawdza, czy cała zawartość jest zaufana przed jej zainstalowaniem. Dzięki temu środowisko będzie bezpieczne przed atakami, w przypadku których lokalizacja pobierania zostanie naruszona. Visual Studio w związku z tym wymaga zainstalowania i aktualizacji kilku standardowych certyfikatów głównych i pośrednich firmy Microsoft na komputerze użytkownika. Jeśli maszyna jest na bieżąco z Windows Update, certyfikaty podpisywania są zwykle aktualne. Jeśli maszyna jest połączona z Internetem, podczas instalacji program Visual Studio odświeżać certyfikaty w razie potrzeby w celu zweryfikowania podpisów plików. Jeśli maszyna jest w trybie offline, certyfikaty muszą zostać odświeżone w inny sposób.

## <a name="how-to-refresh-certificates-when-offline"></a>Jak odświeżać certyfikaty w trybie offline

Istnieją trzy opcje instalowania lub aktualizowania certyfikatów w środowisku offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Opcja 1 — ręczne instalowanie certyfikatów z folderu układu

::: moniker range="vs-2017"

Podczas tworzenia układu [sieci lub](../install/create-a-network-installation-of-visual-studio.md) lokalnej pamięci podręcznej [trybu offline](../install/create-an-offline-installation-of-visual-studio.md)niezbędne certyfikaty są pobierane do folderu Certyfikaty. Następnie możesz ręcznie zainstalować certyfikaty, klikając dwukrotnie każdy z plików certyfikatów, a następnie klikając kreatora Menedżera certyfikatów. Jeśli zostanie poproszony o hasło, pozostaw je puste.

**Aktualizacja:** w przypadku programu Visual Studio 2017 w wersji 15.8 (wersja zapoznawcza 2 lub nowsza) można ręcznie zainstalować certyfikaty, klikając prawym przyciskiem myszy każdy plik certyfikatu, wybierając polecenie Zainstaluj certyfikat, a następnie klikając kreatora Menedżer certyfikatów.

::: moniker-end

::: moniker range=">=vs-2019"

Podczas tworzenia układu [sieci lub](../install/create-a-network-installation-of-visual-studio.md) lokalnej pamięci podręcznej [trybu offline](../install/create-an-offline-installation-of-visual-studio.md)niezbędne certyfikaty są pobierane do folderu Certyfikaty. Certyfikaty można zainstalować ręcznie, klikając prawym przyciskiem myszy każdy plik certyfikatu, wybierając polecenie Zainstaluj certyfikat, a następnie klikając kreatora Menedżera certyfikatów. Jeśli zostanie poproszony o hasło, pozostaw je puste.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Opcja 2 — dystrybucja zaufanych certyfikatów głównych w środowisku przedsiębiorstwa

W przypadku przedsiębiorstw z maszynami w trybie offline, które nie [](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) mają najnowszych certyfikatów głównych, administrator może zaktualizować je za pomocą instrukcji na stronie Konfigurowanie zaufanych katalogów głównych i niedozwolone certyfikaty.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Opcja 3 — instalowanie certyfikatów w ramach wdrożenia skryptowego Visual Studio

W przypadku tworzenia skryptów wdrażania Visual Studio w środowisku offline na klienckich stacjach roboczych należy wykonać następujące kroki:

1. Skopiuj narzędzie [Menedżer certyfikatów](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) do lokalizacji instalacji układu sieciowego lub lokalnej pamięci podręcznej. Certmgr.exe nie jest częścią samego systemu Windows, ale jest dostępny w ramach Windows SDK [.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

2. Utwórz plik wsadowy za pomocą następujących poleceń:

   ```shell
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root
   ```
   
   Alternatywnie możesz utworzyć plik wsadowy, który używa certutil.exe, który jest dostarczany z systemem Windows, za pomocą następujących poleceń:
   
      ```shell
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Wdrażanie pliku wsadowego na kliencie. To polecenie należy uruchomić z procesu z podwyższonym poziomem uprawnień.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Jakie pliki certyfikatów znajdują się w folderze Certyfikaty?

* **plik manifestRootCertificate.cer** zawiera:
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft 2011**
* **manifestCounterSignRootCertificate.cer** **i vs_installer_opc. Plik RootCertificate.cer** zawiera:
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft 2010**
 
Ta Instalator programu Visual Studio wymaga zainstalowania w systemie tylko certyfikatów głównych. Wszystkie te certyfikaty są wymagane dla systemów Windows 7 z dodatkiem Service Pack 1, które nie mają zainstalowanych najnowszych aktualizacji systemu Windows.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Dlaczego certyfikaty z folderu Certyfikaty nie są instalowane automatycznie?

Gdy podpis jest weryfikowany w środowisku online, interfejsy API systemu Windows są używane do pobierania i dodawania certyfikatów do systemu. Podczas tego procesu następuje weryfikacja, czy certyfikat jest zaufany i dozwolony za pośrednictwem ustawień administracyjnych. Ten proces weryfikacji nie może wystąpić w większości środowisk offline. Ręczna instalacja certyfikatów umożliwia administratorom przedsiębiorstwa zapewnienie, że certyfikaty są zaufane i spełniają zasady zabezpieczeń organizacji.

## <a name="checking-if-certificates-are-already-installed"></a>Sprawdzanie, czy certyfikaty są już zainstalowane

Jednym ze sposobów sprawdzenia instalacji systemu jest wykonaj następujące kroki:

1. Uruchom **mmc.exe**.<br/>
  a. Kliknij **pozycję Plik,** a następnie wybierz **pozycję Dodaj/usuń przystawkę.**<br/>
  b. Kliknij dwukrotnie **pozycję Certyfikaty,** wybierz **pozycję Konto komputera,** a następnie kliknij przycisk **Dalej.**<br/>
  c. Wybierz **pozycję Komputer lokalny,** kliknij **przycisk Zakończ,** a następnie kliknij przycisk **OK.**<br/>
  d. Rozwiń **węzł Certyfikaty (komputer lokalny).**<br/>
  e. Rozwiń **Zaufane główne urzędy certyfikacji**, a następnie wybierz **pozycję Certyfikaty.**<br/>
    * Sprawdź tę listę, aby uzyskać niezbędne certyfikaty główne.<br/>

   f. Rozwiń **pozycję Pośrednie urzędy certyfikacji,** a następnie **wybierz pozycję Certyfikaty.**<br/>
    * Sprawdź tę listę wymaganych certyfikatów pośrednich.<br/>

2. Kliknij **pozycję Plik,** a następnie wybierz **pozycję Dodaj/usuń przystawkę.**<br/>
  a. Kliknij dwukrotnie **pozycję Certyfikaty,** wybierz **pozycję Moje konto użytkownika,** kliknij przycisk **Zakończ,** a następnie kliknij przycisk **OK.**<br/>
  b. Rozwiń **węzł Certificates — Current User (Certyfikaty — bieżący użytkownik).**<br/>
  c. Rozwiń **pozycję Pośrednie urzędy certyfikacji,** a następnie **wybierz pozycję Certyfikaty.**<br/>
    * Sprawdź tę listę wymaganych certyfikatów pośrednich.<br/>

Jeśli nazwy certyfikatów nie zostały w kolumnach **Wystawiony dla,** należy je zainstalować.  Jeśli certyfikat pośredni był  tylko w magazynie certyfikatów pośrednich bieżącego użytkownika, jest on dostępny tylko dla zalogowanego użytkownika. Może być konieczne zainstalowanie go dla innych użytkowników.

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

Po zainstalowaniu certyfikatów na komputerze klienckim można zainstalować program [Visual Studio](../install/create-an-offline-installation-of-visual-studio.md#step-3---install-visual-studio-from-the-local-cache)z lokalnej pamięci podręcznej lub wdrożyć program [Visual Studio](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) z udziału układu sieciowego na maszynie klienckiej.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Tworzenie instalacji sieciowej Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

