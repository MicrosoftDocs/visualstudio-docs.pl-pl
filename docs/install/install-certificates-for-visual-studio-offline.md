---
title: Instalowanie certyfikatów wymaganych do instalacji w trybie offline
description: Dowiedz się, jak zainstalować certyfikaty dla instalacji w trybie offline programu Visual Studio.
ms.date: 08/08/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b2570876ddaa03753b1c0d3fb9f9ddc772bbbcb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114662"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Instalowanie certyfikatów wymaganych do instalacji programu Visual Studio w trybie offline

Visual Studio jest przeznaczony przede wszystkim do zainstalowania na komputerze podłączonym do Internetu, ponieważ wiele składników są regularnie aktualizowane. Jednak z niektórych dodatkowych kroków, jest możliwe do wdrożenia programu Visual Studio w środowisku, w którym działające połączenie internetowe jest niedostępne.

Aparat konfiguracji programu Visual Studio instaluje tylko zawartość, która jest zaufana. Odbywa się to poprzez sprawdzenie podpisów Authenticode pobieranej zawartości i sprawdzenie, czy cała zawartość jest zaufana przed zainstalowaniem. Dzięki temu środowisko jest bezpieczne przed atakami, w których lokalizacja pobierania jest zagrożona. Instalator programu Visual Studio wymaga zatem zainstalowania kilku standardowych certyfikatów głównych i pośrednich firmy Microsoft na komputerze użytkownika. Jeśli urządzenie zostało zaktualizowane w usłudze Windows Update, certyfikaty podpisywania są zwykle aktualne. Jeśli komputer jest połączony z Internetem, podczas instalacji program Visual Studio może odświeżyć certyfikaty w razie potrzeby w celu zweryfikowania podpisów plików. Jeśli urządzenie jest w trybie offline, certyfikaty muszą zostać odświeżone w inny sposób.

## <a name="how-to-refresh-certificates-when-offline"></a>Jak odświeżyć certyfikaty w trybie offline

Istnieją trzy opcje instalowania lub aktualizowania certyfikatów w środowisku offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Opcja 1 — ręczne instalowanie certyfikatów z folderu układu

::: moniker range="vs-2017"

Podczas tworzenia układu sieci niezbędne certyfikaty są pobierane do folderu Certyfikaty. Następnie można ręcznie zainstalować certyfikaty, klikając dwukrotnie każdy z plików certyfikatów, a następnie klikając kreatora Menedżera certyfikatów. Jeśli zostaniesz poproszony o podanie hasła, pozostaw to puste.

**Aktualizacja**: W przypadku programu Visual Studio 2017 w wersji 15.8 Preview 2 lub nowszej można ręcznie zainstalować certyfikaty, klikając prawym przyciskiem myszy każdy z plików certyfikatów, wybierając polecenie Zainstaluj certyfikat, a następnie klikając kreatora Menedżera certyfikatów.

::: moniker-end

::: moniker range="vs-2019"

Podczas tworzenia układu sieci niezbędne certyfikaty są pobierane do folderu Certyfikaty. Certyfikaty można zainstalować ręcznie, klikając prawym przyciskiem myszy każdy z plików certyfikatów, wybierając polecenie Zainstaluj certyfikat, a następnie klikając kreatora Menedżera certyfikatów. Jeśli zostaniesz poproszony o podanie hasła, pozostaw to puste.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Opcja 2 — dystrybucja zaufanych certyfikatów głównych w środowisku przedsiębiorstwa

W przypadku przedsiębiorstw z komputerami w trybie offline, które nie mają najnowszych certyfikatów głównych, administrator może użyć instrukcji na stronie [Konfigurowanie zaufanych katalogów głównych i niedozwolonych certyfikatów,](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) aby je zaktualizować.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Opcja 3 — instalowanie certyfikatów w ramach wdrożenia skryptowego programu Visual Studio

Jeśli skrypty wdrożenia programu Visual Studio w środowisku w trybie offline do stacji roboczych klienta, należy wykonać następujące kroki:

::: moniker range="vs-2017"

1. Skopiuj [narzędzie Menedżera certyfikatów](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) \\do udziału instalacyjnego (na przykład server\share\vs2017). Program Certmgr.exe nie jest dołączony do samego systemu Windows, ale jest dostępny jako część [programu Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Utwórz plik wsadowy z następującymi poleceniami:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **Aktualizacja**: W przypadku programu Visual Studio 2017 w wersji 15.8 Wersja zapoznawcza 2 lub nowsza utwórz plik wsadowy za pomocą następujących poleceń:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatywnie należy utworzyć plik wsadowy, który używa pliku certutil.exe, który jest dostarczany z systemem Windows, z następującymi poleceniami:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Wdrażanie pliku wsadowego na kliencie. To polecenie powinno być uruchamiane z procesu podwyższonego poziomu.

::: moniker-end

::: moniker range="vs-2019"

1. Skopiuj [narzędzie Menedżera certyfikatów](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) \\do udziału instalacyjnego (na przykład server\share\vs2019). Program Certmgr.exe nie jest dołączony do samego systemu Windows, ale jest dostępny jako część [programu Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Utwórz plik wsadowy z następującymi poleceniami:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatywnie należy utworzyć plik wsadowy, który używa pliku certutil.exe, który jest dostarczany z systemem Windows, z następującymi poleceniami:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Wdrażanie pliku wsadowego na kliencie. To polecenie powinno być uruchamiane z procesu podwyższonego poziomu.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Jakie są pliki certyfikatów w folderze Certyfikaty?

::: moniker range="vs-2017"

Trzy . Pliki P12 w tym folderze zawierają certyfikat pośredni i certyfikat główny. Większość systemów, które są aktualne w usłudze Windows Update, ma już zainstalowane te certyfikaty.

* **ManifestSignCertificates.p12** zawiera:
  * Certyfikat pośredni: **Podpisywanie kodu pca firmy Microsoft 2011**
    * Niewymagane. Zwiększa wydajność w niektórych scenariuszach, jeśli jest obecny.
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft 2011**
    * Wymagane w systemach Windows 7 z dodatkiem Service Pack 1, w których nie zainstalowano najnowszych aktualizacji systemu Windows.
* **ManifestCounterSignCertificates.p12** zawiera:
  * Certyfikat pośredni: **Microsoft Time-Stamp PCA 2010**
    * Niewymagane. Zwiększa wydajność w niektórych scenariuszach, jeśli jest obecny.
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft 2010**
    * Wymagane dla systemów Windows 7 z dodatkiem Service Pack 1, w których nie są zainstalowane najnowsze aktualizacje systemu Windows.
* **Vs_installer_opc. SignCertificates.p12** zawiera:
  * Certyfikat pośredni: **Podpisywanie kodu pca firmy Microsoft**
    * Wymagane dla wszystkich systemów. Należy zauważyć, że systemy ze wszystkimi aktualizacjami zastosowanymi z usługi Windows Update mogą nie mieć tego certyfikatu.
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft**
    * Wymagany. Ten certyfikat jest dostarczany z systemami z systemem Windows 7 lub nowszym.

**Aktualizacja:** W przypadku programu Visual Studio 2017 w wersji 15.8 Wersja zapoznawcza 2 lub nowsza Instalator programu Visual Studio wymaga instalowania w systemie tylko certyfikatów głównych. Certyfikaty te są przechowywane w plikach cer zamiast .p12.

::: moniker-end

::: moniker range="vs-2019"

* **ManifestSignCertificates.cer** zawiera:
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft 2011**
    * Wymagane w systemach Windows 7 z dodatkiem Service Pack 1, w których nie zainstalowano najnowszych aktualizacji systemu Windows.
* **ManifestCounterSignCertificates.cer** zawiera:
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft 2010**
    * Wymagane dla systemów Windows 7 z dodatkiem Service Pack 1, w których nie są zainstalowane najnowsze aktualizacje systemu Windows.
* **Vs_installer_opc. SignCertificates.cer** zawiera:
  * Certyfikat główny: **Główny urząd certyfikacji firmy Microsoft**
    * Wymagany. Ten certyfikat jest dostarczany z systemami z systemem Windows 7 lub nowszym.

Instalator programu Visual Studio wymaga tylko certyfikatów głównych, które mają być zainstalowane w systemie.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Dlaczego certyfikaty z folderu Certyfikaty nie są instalowane automatycznie?

Po zweryfikowaniu podpisu w środowisku online interfejsy API systemu Windows są używane do pobierania i dodawania certyfikatów do systemu. Podczas tego procesu odbywa się weryfikacja, czy certyfikat jest zaufany i dozwolony za pomocą ustawień administracyjnych. Ten proces weryfikacji nie może wystąpić w większości środowisk w trybie offline. Ręczne instalowanie certyfikatów umożliwia administratorom przedsiębiorstwa zapewnienie, że certyfikaty są zaufane i spełniają zasady zabezpieczeń ich organizacji.

## <a name="checking-if-certificates-are-already-installed"></a>Sprawdzanie, czy certyfikaty są już zainstalowane

Jednym ze sposobów sprawdzenia systemu instalacjonowania jest wykonać następujące kroki:

1. Uruchom **program mmc.exe**.<br/>
  a. Kliknij **pozycję Plik**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.<br/>
  b. Kliknij dwukrotnie pozycję **Certyfikaty**, wybierz pozycję **Konto komputera**, a następnie kliknij przycisk **Dalej**.<br/>
  d. Wybierz **pozycję Komputer lokalny**, kliknij pozycję **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  d. Rozwiń **certyfikaty (komputer lokalny)**.<br/>
  e. Rozwiń pozycję **Zaufane główne urzędy certyfikacji**, a następnie wybierz pozycję **Certyfikaty**.<br/>
    * Sprawdź tę listę niezbędnych certyfikatów głównych.<br/>

   f. Rozwiń **węzeł Pośrednie urzędy certyfikacji**, a następnie wybierz pozycję **Certyfikaty**.<br/>
    * Sprawdź tę listę wymaganych certyfikatów pośrednich.<br/>

2. Kliknij **pozycję Plik**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.<br/>
  a. Kliknij dwukrotnie **pozycję Certyfikaty**, wybierz pozycję **Moje konto użytkownika**, kliknij pozycję **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  b. Rozwiń **certyfikaty — bieżący użytkownik**.<br/>
  d. Rozwiń **węzeł Pośrednie urzędy certyfikacji**, a następnie wybierz pozycję **Certyfikaty**.<br/>
    * Sprawdź tę listę wymaganych certyfikatów pośrednich.<br/>

Jeśli nazwy certyfikatów nie znajdowały się w kolumnach **Wystawione do,** muszą zostać zainstalowane.  Jeśli certyfikat pośredni znajdował się tylko w magazynie bieżących certyfikatów pośrednich **użytkownika,** jest on dostępny tylko dla zalogowanego użytkownika. Może być konieczne zainstalowanie go dla innych użytkowników.

## <a name="install-visual-studio"></a>Instalacja programu Visual Studio

Po zainstalowaniu certyfikatów wdrożenie programu Visual Studio można kontynuować przy użyciu instrukcji z sekcji [Wdrażanie z instalacji sieciowej](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) na stronie "Tworzenie instalacji sieciowej programu Visual Studio".

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
