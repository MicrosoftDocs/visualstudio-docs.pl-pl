---
title: Instalowanie certyfikatów wymaganych do instalacji w trybie offline
description: Dowiedz się, jak zainstalować certyfikaty dla instalacji w trybie offline programu Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4ef5df077aabb02c9e9a4b46b0cfcbda76263b72
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58789344"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio

Program Visual Studio jest przeznaczony głównie do zainstalowania na komputerze połączonym z Internetem, ponieważ wiele składników są regularnie aktualizowane. Jednak za pomocą kilka dodatkowych kroków, istnieje możliwość wdrażanie programu Visual Studio w środowisku, w przypadku, gdy działającego połączenia internetowego jest niedostępny.

Aparat Instalatora programu Visual Studio instaluje tylko zawartość, która jest zaufana. Dzieje się tak, sprawdzając sygnatur Authenticode zawartości pobierany i weryfikowanie, czy cała zawartość jest zaufany, przed zainstalowaniem. Dzięki temu środowiska przed atakami gdzie zostanie naruszony lokalizacji pobierania. Program Visual Studio Instalator w związku z tym wymaga zainstalowania kilka standardowych główne firmy Microsoft i certyfikatów pośrednich i w górę do daty na komputerze użytkownika. Jeśli komputer został zachowany na bieżąco z usługą Windows Update, certyfikaty podpisywania zwykle są aktualne. Jeśli komputer jest połączony z Internetem, podczas instalacji programu Visual Studio może odświeżyć certyfikaty w razie do weryfikowania podpisów plików. Jeśli komputer jest w trybie offline, certyfikaty musi być odświeżane w inny sposób.

## <a name="how-to-refresh-certificates-when-offline"></a>Jak odświeżyć certyfikaty, gdy jest w trybie offline

Istnieją trzy opcje instalowania lub aktualizowania certyfikatów w środowisku, w trybie offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Opcja 1 — ręcznie instalować certyfikaty z folderu układu

::: moniker range="vs-2017"

Podczas tworzenia układu sieci wymagane certyfikaty zostaną pobrane do folderu certyfikatów. Następnie może ręcznie instalować certyfikaty dwukrotne kliknięcie każdego z plików certyfikatów, a następnie klikając polecenie za pomocą Kreatora Menedżera certyfikatów. Jeśli pojawi się pytanie o hasło, pozostaw to pole puste.

**Aktualizacja**: Dla programu Visual Studio 2017 w wersji 15.8 w wersji Preview 2 lub nowszej, można ręcznie zainstalować certyfikaty, kliknij prawym przyciskiem myszy każdy plik certyfikatu, wybierając Zainstaluj certyfikat, a następnie klikając za pomocą Kreatora Menedżera certyfikatów.

::: moniker-end

::: moniker range="vs-2019"

Podczas tworzenia układu sieci wymagane certyfikaty zostaną pobrane do folderu certyfikatów. Certyfikaty możesz zainstalować ręcznie, klikając prawym przyciskiem myszy każdy plik certyfikatu, wybierając Zainstaluj certyfikat, a następnie klikając za pomocą Kreatora Menedżera certyfikatów. Jeśli pojawi się pytanie o hasło, pozostaw to pole puste.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Opcja 2 — rozpowszechniania zaufanych głównych certyfikatów w środowisku przedsiębiorstwa

Dla przedsiębiorstw mających maszyny w trybie offline, które nie mają najnowsze certyfikaty główne, administrator może użyć instrukcji na [Konfigurowanie zaufanych certyfikatów głównych i niedopuszczalne certyfikaty](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) strony, aby je zaktualizować.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Opcja 3 — certyfikaty Zainstaluj jako część inicjowanych przez skrypty wdrażania programu Visual Studio

Jeśli to skryptów wdrażania programu Visual Studio w środowisku offline na klienckich stacjach roboczych, powinni wykonać następujące czynności:

::: moniker range="vs-2017"

1. Kopiuj [narzędzie Menedżer certyfikatów](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) w udziale instalacji (na przykład \\server\share\vs2017). Certmgr.exe nie jest częścią Windows, ale jest dostępny jako część [zestawu Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Utwórz plik wsadowy za pomocą następujących poleceń:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **Aktualizacja**: Dla programu Visual Studio 2017 w wersji Preview należy zachować 15,8 2 lub nowszego, utworzyć plik wsadowy za pomocą następujących poleceń:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatywnie można utworzyć plik wsadowy, który używa certutil.exe, który jest dostarczany z Windows, za pomocą następujących poleceń:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Wdróż plik wsadowy do klienta. To polecenie można uruchamiać z procesów z podwyższonym poziomem uprawnień.

::: moniker-end

::: moniker range="vs-2019"

1. Kopiuj [narzędzie Menedżer certyfikatów](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) w udziale instalacji (na przykład \\server\share\vs2019). Certmgr.exe nie jest częścią Windows, ale jest dostępny jako część [zestawu Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Utwórz plik wsadowy za pomocą następujących poleceń:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Alternatywnie można utworzyć plik wsadowy, który używa certutil.exe, który jest dostarczany z Windows, za pomocą następujących poleceń:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Wdróż plik wsadowy do klienta. To polecenie można uruchamiać z procesów z podwyższonym poziomem uprawnień.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Co to są w nim certyfikaty pliki certyfikatów?

::: moniker range="vs-2017"

3. Pliki p12, w tym folderze każdego zawierają pośredniego certyfikatu i certyfikatu głównego. Certyfikaty zainstalowane zostały większości systemów, które są aktualne z usługą Windows Update.

* **ManifestSignCertificates.p12** zawiera:
    * Pośredniego certyfikatu: **Podpisywanie 2011 UPW kodu firmy Microsoft**
        * Nie jest wymagane. Zwiększa wydajność w niektórych scenariuszach, jeśli jest obecny.
    * Certyfikat główny: **Microsoft główny urząd certyfikacji 2011**
        * Wymagany w systemach Windows 7 z dodatkiem SP1, które nie mają zainstalowanych najnowszych aktualizacji Windows.
* **ManifestCounterSignCertificates.p12** zawiera:
    * Pośredniego certyfikatu: **Microsoft Time-Stamp PCA 2010**
        * Nie jest wymagane. Zwiększa wydajność w niektórych scenariuszach, jeśli jest obecny.
    * Certyfikat główny: **Microsoft główny urząd certyfikacji 2010**
        * Wymagany dla systemów Windows 7 z dodatkiem SP1, które nie mają zainstalowanych najnowszych aktualizacji Windows.
* **Vs_installer_opc. SignCertificates.p12** zawiera:
    * Pośredniego certyfikatu: **Podpisywanie UPW kodu firmy Microsoft**
        * Wymagane we wszystkich systemach. Należy pamiętać, że systemy za pomocą wszystkie aktualizacje stosowane z witryny Windows Update nie mogą mieć ten certyfikat.
    * Certyfikat główny: **Microsoft główny urząd certyfikacji**
        * Wymagana. Ten certyfikat jest dostarczany z komputerów z systemami Windows 7 lub nowszy.

**Aktualizacja**: Dla programu Visual Studio 2017 w wersji Preview należy zachować 15,8 2 lub nowszego, Instalator programu Visual Studio wymaga tylko certyfikaty główne do zainstalowania w systemie.

::: moniker-end

::: moniker range="vs-2019"

* **ManifestSignCertificates.p12** zawiera:
    * Pośredniego certyfikatu: **Podpisywanie 2011 UPW kodu firmy Microsoft**
        * Nie jest wymagane. Zwiększa wydajność w niektórych scenariuszach, jeśli jest obecny.
    * Certyfikat główny: **Microsoft główny urząd certyfikacji 2011**
        * Wymagany w systemach Windows 7 z dodatkiem SP1, które nie mają zainstalowanych najnowszych aktualizacji Windows.
* **ManifestCounterSignCertificates.p12** zawiera:
    * Pośredniego certyfikatu: **Microsoft Time-Stamp PCA 2010**
        * Nie jest wymagane. Zwiększa wydajność w niektórych scenariuszach, jeśli jest obecny.
    * Certyfikat główny: **Microsoft główny urząd certyfikacji 2010**
        * Wymagany dla systemów Windows 7 z dodatkiem SP1, które nie mają zainstalowanych najnowszych aktualizacji Windows.
* **Vs_installer_opc. SignCertificates.p12** zawiera:
    * Pośredniego certyfikatu: **Podpisywanie UPW kodu firmy Microsoft**
        * Wymagane we wszystkich systemach. Należy pamiętać, że systemy za pomocą wszystkie aktualizacje stosowane z witryny Windows Update nie mogą mieć ten certyfikat.
    * Certyfikat główny: **Microsoft główny urząd certyfikacji**
        * Wymagana. Ten certyfikat jest dostarczany z komputerów z systemami Windows 7 lub nowszy.

Instalator programu Visual Studio wymaga tylko certyfikaty główne do zainstalowania w systemie.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Dlaczego są certyfikaty z folderu certyfikaty nie są instalowane automatycznie?

Po podpis jest weryfikowany w środowisku, w trybie online, interfejsy API Windows są używane do pobierania i Dodaj certyfikaty do systemu. Weryfikacja, czy certyfikat jest zaufany, za pomocą ustawień administracyjnych występuje w trakcie tego procesu. Ten proces sprawdzania poprawności nie może wystąpić w środowiskach najbardziej w trybie offline. Ręczne instalowanie certyfikatów umożliwia Administratorzy przedsiębiorstwa w celu zapewnienia certyfikaty są zaufane i zgodne z zasadami zabezpieczeń organizacji.

## <a name="checking-if-certificates-are-already-installed"></a>Sprawdzanie, czy certyfikaty są już zainstalowany

Jest jednym ze sposobów, aby sprawdzić instalację systemu wykonaj następujące kroki:

1. Uruchom **mmc.exe**.<br/>
  a. Kliknij przycisk **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.<br/>
  b. Kliknij dwukrotnie **certyfikaty**, wybierz opcję **konto komputera**, a następnie kliknij przycisk **dalej**.<br/>
  c. Wybierz **komputera lokalnego**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  d. Rozwiń **certyfikaty (komputer lokalny)**.<br/>
  e. Rozwiń **zaufane główne urzędy certyfikacji**, a następnie wybierz pozycję **certyfikaty**.<br/>
    * Sprawdź tę listę pod kątem certyfikatów głównych niezbędne.<br/>

   f. Rozwiń **pośrednie urzędy certyfikacji**, a następnie wybierz pozycję **certyfikaty**.<br/>
    * Sprawdź tę listę pod kątem wymaganych certyfikatów pośrednich.<br/>

2. Kliknij przycisk **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.<br/>
  a. Kliknij dwukrotnie **certyfikaty**, wybierz opcję **Moje konto użytkownika**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  b. Rozwiń **Certyfikaty — bieżący użytkownik**.<br/>
  c. Rozwiń **pośrednie urzędy certyfikacji**, a następnie wybierz pozycję **certyfikaty**.<br/>
    * Sprawdź tę listę pod kątem wymaganych certyfikatów pośrednich.<br/>

Jeśli nazwy certyfikatów nie były w **wystawiony dla** kolumn muszą być zainstalowane.  Jeśli pośredniego certyfikatu tylko w **bieżącego użytkownika** certyfikat pośredniego przechowywania, a następnie jest dostępna tylko dla użytkownika, który jest zalogowany. Użytkownik może być konieczne zainstalowanie go innym użytkownikom.

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

Po zainstalowaniu certyfikatów, za pomocą instrukcji z kontynuacją wdrożenia programu Visual Studio [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) części "Tworzenie instalacji sieciowej programu Visual Studio".

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
