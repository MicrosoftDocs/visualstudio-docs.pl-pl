---
title: Instalowanie certyfikatów dla instalacji w trybie offline
description: Dowiedz się, jak zainstalować certyfikaty dla instalacji w trybie offline programu Visual Studio.
ms.date: 03/29/2021
ms.custom: seodec18, SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0d8441b0a4b8acba3f24f60d5ea8dc7030b79253
ms.sourcegitcommit: 22789927ec8e877b7d2b67a555d6df97d84103e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2021
ms.locfileid: "105981293"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Zainstaluj certyfikaty wymagane do instalacji w trybie offline programu Visual Studio

Program Visual Studio jest przeznaczony głównie do zainstalowania na komputerze połączonym z Internetem, ponieważ wiele składników jest regularnie aktualizowanych. Jednak w przypadku niektórych dodatkowych kroków można wdrożyć program Visual Studio w środowisku, w którym działające połączenie internetowe jest niedostępne.

Aparat Instalatora programu Visual Studio instaluje tylko zawartość, która jest zaufana. Robi to, sprawdzając podpisy Authenticode pobieranej zawartości i sprawdzając, czy cała zawartość jest zaufana przed jej zainstalowaniem. Pozwala to na bezpieczne środowisko przed atakami, w których naruszyć bezpieczeństwo lokalizacji pobierania. W związku z tym Instalator programu Visual Studio wymaga, aby kilka standardowych i pośrednich certyfikatów firmy Microsoft były instalowane i aktualne na komputerze użytkownika. Jeśli komputer jest aktualny z Windows Update, certyfikaty podpisywania zazwyczaj są aktualne. Jeśli komputer jest połączony z Internetem, podczas instalacji program Visual Studio może odświeżyć certyfikaty w razie potrzeby w celu zweryfikowania podpisów plików. Jeśli komputer jest w trybie offline, certyfikaty muszą być odświeżane w inny sposób.

## <a name="how-to-refresh-certificates-when-offline"></a>Jak odświeżyć certyfikaty w trybie offline

Istnieją trzy opcje instalowania lub aktualizowania certyfikatów w środowisku trybu offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Opcja 1 — Ręczne instalowanie certyfikatów z folderu układu

::: moniker range="vs-2017"

Podczas tworzenia [układu sieciowego](../install/create-a-network-installation-of-visual-studio.md) lub [lokalnej pamięci podręcznej w trybie offline](../install/create-an-offline-installation-of-visual-studio.md)wymagane certyfikaty są pobierane do folderu certyfikaty. Następnie można ręcznie zainstalować certyfikaty, klikając dwukrotnie każdy plik certyfikatu, a następnie klikając kreatora Menedżera certyfikatów. Jeśli zostanie wyświetlony monit o podanie hasła, pozostaw to pole puste.

**Aktualizacja**: dla programu Visual Studio 2017 w wersji 15,8 Preview 2 lub nowszej można ręcznie zainstalować certyfikaty, klikając prawym przyciskiem myszy poszczególne pliki certyfikatów, wybierając pozycję Zainstaluj certyfikat, a następnie klikając kreatora Menedżera certyfikatów.

::: moniker-end

::: moniker range="vs-2019"

Podczas tworzenia [układu sieciowego](../install/create-a-network-installation-of-visual-studio.md) lub [lokalnej pamięci podręcznej w trybie offline](../install/create-an-offline-installation-of-visual-studio.md)wymagane certyfikaty są pobierane do folderu certyfikaty. Certyfikaty można zainstalować ręcznie, klikając prawym przyciskiem myszy każdy plik certyfikatu, wybierając pozycję Zainstaluj certyfikat, a następnie klikając kreatora Menedżera certyfikatów. Jeśli zostanie wyświetlony monit o podanie hasła, pozostaw to pole puste.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Opcja 2 — dystrybuowanie zaufanych certyfikatów głównych w środowisku przedsiębiorstwa

W przypadku przedsiębiorstw z maszynami w trybie offline, które nie mają najnowszych certyfikatów głównych, administrator może użyć instrukcji na stronie [Konfigurowanie zaufanych katalogów głównych i niedozwolonych certyfikatów](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) , aby je zaktualizować.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Opcja 3 — Instalowanie certyfikatów w ramach wdrożenia skryptowego programu Visual Studio

Jeśli tworzysz skryptowo wdrożenie programu Visual Studio w środowisku offline na klienckich stacjach roboczych, wykonaj następujące kroki:

1. Skopiuj [narzędzie Menedżer certyfikatów](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) do lokalizacji instalacji w układzie sieciowym lub w lokalnej pamięci podręcznej. Certmgr.exe nie jest uwzględniony jako część samego systemu Windows, ale jest dostępny jako część [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Utwórz plik wsadowy za pomocą następujących poleceń:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root
   ```
   
   Alternatywnie można utworzyć plik wsadowy, który używa certutil.exe, który jest dostarczany z systemem Windows, przy użyciu następujących poleceń:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Wdróż plik wsadowy na komputerze klienckim. To polecenie powinno być uruchamiane z procesu z podwyższonym poziomem uprawnień.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Jakie są pliki certyfikatów w folderze certyfikaty?

* **manifestRootCertificate. cer** zawiera:
  * Certyfikat główny: **główny urząd certyfikacji firmy Microsoft 2011**
* **manifestCounterSignRootCertificate. cer** i **vs_installer_opc. RootCertificate. cer** zawiera:
  * Certyfikat główny: **główny urząd certyfikacji firmy Microsoft 2010**
 
Instalator programu Visual Studio wymaga zainstalowania tylko certyfikatów głównych w systemie. Wszystkie te certyfikaty są wymagane w systemach Windows 7 z dodatkiem Service Pack 1, na których nie zainstalowano najnowszych aktualizacji systemu Windows.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Dlaczego certyfikaty z folderu certyfikaty nie są instalowane automatycznie?

W przypadku zweryfikowania podpisu w środowisku online interfejsy API systemu Windows są używane do pobierania i dodawania certyfikatów do systemu. Sprawdzenie, czy certyfikat jest zaufany i jest dozwolony za pośrednictwem ustawień administracyjnych, występuje w trakcie tego procesu. Ten proces weryfikacji nie może wystąpić w większości środowisk w trybie offline. Ręczne zainstalowanie certyfikatów pozwala administratorom przedsiębiorstwa upewnić się, że certyfikaty są zaufane i spełniają zasady zabezpieczeń swojej organizacji.

## <a name="checking-if-certificates-are-already-installed"></a>Sprawdzanie, czy certyfikaty są już zainstalowane

Jednym ze sposobów sprawdzenia instalacji systemu jest wykonanie następujących czynności:

1. Uruchom **mmc.exe**.<br/>
  a. Kliknij pozycję **plik**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.<br/>
  b. Kliknij dwukrotnie pozycję **Certyfikaty**, wybierz pozycję **konto komputera**, a następnie kliknij przycisk **dalej**.<br/>
  c. Wybierz pozycję **komputer lokalny**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  d. Rozwiń węzeł **Certyfikaty (komputer lokalny)**.<br/>
  e. Rozwiń węzeł **Zaufane główne** urzędy certyfikacji, a następnie wybierz pozycję **Certyfikaty**.<br/>
    * Sprawdź tę listę dla wymaganych certyfikatów głównych.<br/>

   f. Rozwiń węzeł **urzędy certyfikacji pośrednich**, a następnie wybierz pozycję **Certyfikaty**.<br/>
    * Sprawdź tę listę dla wymaganych certyfikatów pośrednich.<br/>

2. Kliknij pozycję **plik**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.<br/>
  a. Kliknij dwukrotnie pozycję **Certyfikaty**, wybierz pozycję **Moje konto użytkownika**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  b. Rozwiń węzeł **Certyfikaty — bieżący użytkownik**.<br/>
  c. Rozwiń węzeł **urzędy certyfikacji pośrednich**, a następnie wybierz pozycję **Certyfikaty**.<br/>
    * Sprawdź tę listę dla wymaganych certyfikatów pośrednich.<br/>

Jeśli nazwy certyfikatów nie znajdują się w kolumnach **wystawiony dla** , muszą być zainstalowane.  Jeśli certyfikat pośredni był tylko w magazynie certyfikatów pośredniego **użytkownika** , jest dostępny tylko dla zalogowanego użytkownika. Może być konieczne zainstalowanie go dla innych użytkowników.

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

Po zainstalowaniu certyfikatów na komputerze klienckim, możesz [zainstalować program Visual Studio z lokalnej pamięci podręcznej](../install/create-an-offline-installation-of-visual-studio.md#step-3---install-visual-studio-from-the-local-cache)lub [wdrożyć program Visual Studio z udziału układu sieciowego](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) na komputerze klienckim.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

