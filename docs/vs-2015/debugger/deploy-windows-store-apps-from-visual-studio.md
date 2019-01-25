---
title: Wdrażanie aplikacji Windows Store
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
ms.openlocfilehash: 520113d97bdf41d750cad340c0ab8868eb85f603
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805220"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Wdrażanie aplikacji Windows Store za pomocą programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko Windows] (.. /Image/windows_only_content.png "windows_only_content")

 Funkcjonalność wdrożenia programu Visual Studio tworzy i rejestruje aplikacje Windows Store, które są tworzone za pomocą programu Visual Studio na urządzeniu docelowym. Dokładnie, jak aplikacja jest zarejestrowana, zależy od tego, czy urządzenie docelowe jest lokalnym lub zdalnym:

- Gdy element docelowy jest komputera lokalnego programu Visual Studio, Visual Studio rejestruje aplikacji z poziomu folderu jego kompilacji.

- Gdy element docelowy jest urządzenie zdalne, Visual Studio kopiuje pliki wymagane do maszyny zdalnej i rejestruje aplikację na tym urządzeniu.

  Wdrożenia jest automatycznie podczas debugowania aplikacji w programie Visual Studio przy użyciu **Rozpocznij debugowanie** opcji (klawiatury: F5) lub **Rozpocznij bez debugowania** opcji (klawiatury: CTRL + F5). Można także wdrożyć aplikację ręcznie. Ręczne wdrażanie jest przydatne w następujących scenariuszach:

- Ad hoc testów na komputerze lokalnym lub zdalnym.

- Wdrażanie aplikacji, która zostanie uruchomiona w innej aplikacji, który chcesz debugować.

- Wdrażanie aplikacji, która będzie debugowany, gdy jest ona uruchamiana przez inną aplikację lub metody.

##  <a name="BKMK_In_this_topic"></a> W tym temacie
 W tym temacie nauczysz:

 [Jak wdrożyć aplikację Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Jak określić urządzenie zdalne](#BKMK_How_to_specify_a_remote_device)

 [Opcje wdrażania](#BKMK_Deployment_options)

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak wdrożyć aplikację Windows Store
 Ręczne wdrażanie aplikacji jest prostym procesem:

1.  Jeśli są wdrażane na urządzeniu zdalnym, należy określić nazwę lub adres IP urządzenia na stronie właściwości projektu z projektu do uruchamiania aplikacji. (Kroki, aby zrobić to są wymienione dalszych szczegółów, w tym temacie).

2.  Na pasku narzędzi programu Visual Studio debugger wybierz cel wdrożenia z listy rozwijanej obok **Rozpocznij debugowanie** przycisku.

     ![Uruchom na lokalnym komputerze](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3.  Na **kompilacji** menu, wybierz **wdrażania**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Jak określić urządzenie zdalne
 **Wymagania wstępne**

 Aby wdrożyć aplikację na urządzeniu zdalnym:

-   Licencja dewelopera musi być zainstalowany na urządzeniu zdalnym.

-   Narzędzia zdalne programu Visual Studio musi być zainstalowany na urządzeniu zdalnym, i Monitor zdalnego debugowania musi być uruchomiona.

     Wdrożenie używa zdalny debuger kanał sieciowy do wysyłania plików aplikacji na urządzeniu zdalnym.

#### <a name="to-specify-a-remote-device"></a>Aby określić urządzenie zdalne

1. Na stronie właściwości debugowania projektu startowego Określ nazwę lub adres IP elementu docelowego wdrażania zdalnego.

2. Aby otworzyć stronę właściwości debugowania, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.

3. Następnie wybierz **debugowania** węzła w oknie właściwości strony.

4. Możesz wpisać nazwę lub adres IP urządzenia zdalnego lub można wybrać urządzenie w **wybierz połączenie ze zdalnym debugerem** okno dialogowe.

    ![Okno dialogowe Wybierz połączenie ze zdalnym debugerem](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Wybierz połączenie ze zdalnym debugerem** okno dialogowe wyświetla urządzenia w podsieci sieci lokalnej i dowolnego urządzenia podłączonego bezpośrednio do maszyny programu Visual Studio za pomocą kabla Ethernet.

   **Określanie urządzenie zdalne, na stronie projektu języka Visual C++ lub JavaScript**

   ![C&#43; &#43; właściwości dla zdalnego debugowania projektu](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Wybierz **zdalny debuger** z **debuger do uruchomienia** listy.

6. Wprowadź nazwę sieciową urządzenia zdalnego w **NazwaKomputera** pole. Alternatywnie można wybrać strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym Wybierz połączenie ze zdalnym debugerem.

   **Określanie urządzenie zdalne na stronie projektu Visual C# i Visual Basic**

   ![Właściwości projektu dla zdalnego debugowania zarządzane](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.

8. Wprowadź nazwę sieciową urządzenia zdalnego w **maszyny zdalnej** lub przycisk **znaleźć** do wyboru urządzenia z **wybierz połączenie ze zdalnym debugerem** okno dialogowe.

##  <a name="BKMK_Deployment_options"></a> Opcje wdrażania
 Można ustawić następujące opcje wdrażania na stronie właściwości debugowania projektu startowego.

 **Zezwalaj na sprzężenie zwrotne sieci** ze względów bezpieczeństwa [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikację, która jest zainstalowana w standardowy sposób wykonywania wywołań sieci na urządzeniu jest zainstalowany na jest niedozwolone. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji do [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], należy przetestować aplikację bez zwolnienia.

 Aby usunąć wykluczenie sprzężenie zwrotne sieci z poziomu aplikacji:

- Na stronie właściwości języka C# i VB debugowania wyczyść **Zezwalaj na sprzężenie zwrotne sieci** pole wyboru.

- Na stronie właściwości języka JavaScript i debugowania, ustaw **Zezwalaj na sprzężenie zwrotne sieci** wartość **nie**.

  **Nie uruchamiaj, ale Debuguj kod przy rozpoczęciu (C# i VB) / uruchamianie aplikacji (JavaScript i C++)** umożliwia skonfigurowanie wdrażania do automatycznego uruchamiania sesji debugowania, gdy aplikacja jest uruchamiana:

- Na stronie właściwości języka C# i VB debugowania, sprawdź **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** pole wyboru.

- Na stronie właściwości języka JavaScript i debugowania, ustaw **Uruchom aplikację** wartość **tak**.

## <a name="see-also"></a>Zobacz też
 [Uruchamianie aplikacji w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
