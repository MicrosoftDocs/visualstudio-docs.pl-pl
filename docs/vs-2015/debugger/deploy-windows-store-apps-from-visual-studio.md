---
title: Wdrażanie aplikacji ze sklepu Windows
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177477"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Wdrażanie aplikacji ze Sklepu Windows w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko systemu Windows] (.. /Image/windows_only_content.png "windows_only_content")

 Funkcja wdrażania programu Visual Studio kompiluje i rejestruje aplikacje ze sklepu Windows utworzone za pomocą programu Visual Studio na urządzeniu docelowym. Dokładnie sposób rejestracji aplikacji zależy od tego, czy urządzenie docelowe jest lokalne, czy zdalne:

- Gdy obiektem docelowym jest lokalna maszyna programu Visual Studio, program Visual Studio rejestruje aplikację z folderu Build.

- Gdy obiektem docelowym jest urządzenie zdalne, program Visual Studio kopiuje wymagane pliki na maszynę zdalną i rejestruje aplikację na tym urządzeniu.

  Wdrożenie jest automatyczne podczas debugowania aplikacji z programu Visual Studio przy użyciu opcji **Rozpocznij debugowanie** (klawiatura: F5) lub opcji **Rozpocznij bez debugowania** (klawiatura: CTRL + F5). Aplikację można również wdrożyć ręcznie. Ręczne wdrażanie jest przydatne w następujących scenariuszach:

- Testowanie ad hoc na komputerze lokalnym lub zdalnym.

- Wdrażanie aplikacji, która będzie uruchamiać inną aplikację, którą chcesz debugować.

- Wdrażanie aplikacji, która będzie debugowana, gdy zostanie uruchomiona przez inną aplikację lub metodę.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 W tym temacie możesz poznać następujące informacje:

 [Jak wdrożyć aplikację ze sklepu Windows](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Jak określić urządzenie zdalne](#BKMK_How_to_specify_a_remote_device)

 [Opcje wdrożenia](#BKMK_Deployment_options)

## <a name="how-to-deploy-a-windows-store-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak wdrożyć aplikację ze sklepu Windows
 Ręczne wdrażanie aplikacji to prosty proces:

1. W przypadku wdrażania na urządzeniu zdalnym należy określić nazwę lub adres IP urządzenia na stronie projekt właściwości projektu startowego aplikacji. (Kroki, które należy wykonać, przedstawiono w dalszej części tego tematu).

2. Na pasku narzędzi debugera programu Visual Studio wybierz element docelowy wdrożenia z listy rozwijanej obok przycisku **Rozpocznij debugowanie** .

     ![Uruchom na komputerze lokalnym](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. W menu **kompilacja** wybierz polecenie **Wdróż** .

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Jak określić urządzenie zdalne
 **Wymagania wstępne**

 Aby wdrożyć aplikację na urządzeniu zdalnym:

- Na urządzeniu zdalnym musi być zainstalowana licencja dewelopera.

- Narzędzia zdalne programu Visual Studio muszą być zainstalowane na urządzeniu zdalnym, a Monitor zdalnego debugowania musi być uruchomiona.

     Wdrożenie używa kanału sieciowego debugera zdalnego do wysyłania plików aplikacji do zdalnego urządzenia.

#### <a name="to-specify-a-remote-device"></a>Aby określić urządzenie zdalne

1. Na stronie właściwości debugowania projektu startowego Określ nazwę lub adres IP miejsca docelowego wdrożenia zdalnego.

2. Aby otworzyć stronę właściwości debugowania, wybierz projekt w Eksplorator rozwiązań a następnie wybierz **Właściwości** z menu skrótów.

3. Następnie wybierz węzeł **debugowanie** w oknie strony właściwości.

4. Można wpisać nazwę lub adres IP urządzenia zdalnego lub wybrać urządzenie w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .

    ![Okno dialogowe Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    W oknie dialogowym **Wybieranie połączenia debugera zdalnego** są wyświetlane urządzenia w podsieci sieci lokalnej i każde urządzenie połączone bezpośrednio z maszyną programu Visual Studio za pomocą kabla Ethernet.

   **Określanie urządzenia zdalnego na stronie projektu JavaScript lub Visual C++**

   ![C&#43;&#43; właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Wybierz **zdalny debuger** z listy **debuger do uruchomienia** .

6. Wprowadź nazwę sieciową urządzenia zdalnego w polu **Nazwa komputera** . Możesz też wybrać strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym Wybierz połączenie ze zdalnym debugerem.

   **Określanie urządzenia zdalnego w Visual C# i Visual Basic stronie projektu**

   ![Zarządzane właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Wybierz pozycję **maszyna zdalna** z listy **urządzeń docelowych** .

8. Wprowadź nazwę sieciową urządzenia zdalnego w polu **maszyna zdalna** lub kliknij przycisk **Znajdź** , aby wybrać urządzenie w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Opcje wdrażania
 Można ustawić następujące opcje wdrażania na stronie właściwości debugowania projektu startowego.

 **Zezwalaj na sprzężenie zwrotne sieci** Ze względów bezpieczeństwa [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacja zainstalowana w standardowym sposobie nie może wykonywać wywołań sieciowych na urządzeniu, na którym jest ono zainstalowane. Domyślnie wdrożenie programu Visual Studio tworzy wykluczenie z tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia testowanie procedur komunikacji na pojedynczym komputerze. Przed przesłaniem aplikacji do programu należy [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] przetestować aplikację bez wykluczania.

 Aby usunąć wykluczenie sprzężenia zwrotnego sieci z aplikacji:

- Na stronie właściwości debugowania C# i VB wyczyść pole wyboru **Zezwalaj na sprzężenie zwrotne sieci** .

- Na stronie właściwości JavaScript i Debuguj ustaw wartość opcji **Zezwalaj na sprzężenie zwrotne sieci** na **nie**.

  **Nie uruchamiaj, ale Debuguj mój kod podczas uruchamiania (C# i VB)/uruchamiania aplikacji (JavaScript i C++)** Aby skonfigurować wdrożenie w celu automatycznego uruchamiania sesji debugowania podczas uruchamiania aplikacji:

- Na stronie właściwości debugowania C# i VB zaznacz pole wyboru nie **uruchamiaj, ale Debuguj mój kod podczas uruchamiania** .

- Na stronie właściwości JavaScript i Debuguj ustaw wartość opcji **Uruchom aplikację** na **tak**.

## <a name="see-also"></a>Zobacz też
 [Uruchamianie aplikacji w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
