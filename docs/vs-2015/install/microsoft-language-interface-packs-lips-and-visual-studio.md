---
title: Pakiety języka Microsoft interfejsu (użytkownika LIP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 647935dce06d74b29271af130686a10fb8cfc1e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065041"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Pakiety języka interfejsu użytkownika (LIP) firmy Microsoft a program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą pakietu interfejsu Windows Language (LIP), można zainstalować Windows w wersji językowej, a następnie zainstaluj różne pakiety języka interfejsu użytkownika. Pakiety języka interfejsu użytkownika udostępniają interfejs zlokalizowane użytkownika (UI) dla systemu operacyjnego. Na przykład można zainstalować japoński pakiet językowy na angielskiej wersji systemu Windows i następnie zmianę języka interfejsu użytkownika Windows między kalendarza japońskiego i język angielski. Za pomocą lip, może mieć wielu wersji językowych programu Windows na jednym komputerze.

 Na komputerach, które mają LIP i wiele wersji językowych programu Visual Studio zmiana Windows Ustawienia języka wyświetlania powoduje zarówno Windows, jak i programu Visual Studio po zainstalowaniu zgodnych pakietów językowych.

## <a name="limitations-of-multi-language-installations"></a>Ograniczenia urządzeń wiele języków
 Podczas instalowania różnych wersji językowych programu Visual Studio na tym samym komputerze, można przełączyć tylko języki między wersjami dopasowania. Na przykład jeśli masz angielskiej wersji Express zainstalowane, niemieckiej wersji Express jest zainstalowany i zainstalowany w wersji Professional, języków można przełączyć tylko w przypadku wersji Express, a nie w wersji Professional.

 Visual Studio korzysta z pakietu językowego ujednoliconego. Aby zainstalować więcej niż jedną wersję językową tych produktów, należy najpierw zainstalować produkt z pełną obsługą języka, a następnie zainstaluj jeden lub więcej pakietów językowych.

> [!NOTE]
>  Program Visual Studio nie obsługuje instalowanie wielu wersji językowych produktu z pełną obsługą języka na tym samym komputerze. Po zainstalowaniu jeden produkt z pełną obsługą języka, należy dodać wersje językowe przy użyciu pakietów językowych. Nadal można zainstalować wiele produktów pełną obsługą języka w wersji Express na tym samym komputerze.

### <a name="support-for-code-pages"></a>Obsługa stron kodowych
 Niektóre narzędzia programu Visual Studio nie są wyświetlane tekst poprawnie, gdy tekst zawiera znaki, które nie znajdują się w bieżącej stronie kodowej. Zamiast tego są wyświetlane znaki zapytania lub tekstu jest uszkodzony. Uwzględnione są następujące narzędzia lub obszarów:

-   Lokacje wdrożyć przy użyciu protokołu FTP.

-   Nazwy komputerów spoza zestawu ASCII w niektóre kontrolki.

-   Narzędzia wiersza polecenia, które Uruchom poza programem Visual Studio.

-   Kreator migracji programu Visual Basic.

-   Kontener testu kontrolki ActiveX.

-   OLE/COM Object Viewer.

-   Narzędzia debugowania w sieci Web interfejsu ISAPI.

-   Projekty aplikacji MFC, które mają zawartość pomocy w formacie HTML.

-   Visual SourceSafe / interfejsu użytkownika SCCI powraca do języka angielskiego po stronie niezgodnego kodu.

-   Visual SourceSafe nie obsługuje nazwy plików Unicode.

-   Zdefiniowane przez użytkownika końcowego znaków (Korzystanie z prywatnej strefy) nie może służyć jako tokenów/identyfikatorów.

-   Nie można wyświetlić znaki alfabetu łacińskiego Extended-B w niektórych okien narzędzi, gdy strona kodowa Windows jest ustawiony język wschodnioazjatyckich programu Visual Studio.

-   Domyślnego symbolu dla niektórych znaków mogą być wyświetlane uruchomienia tekstu, które składają się ze znaków z wielu skryptów języka.

-   Kopiowanie i wklejanie skryptów złożonych ciągów do wspólnych formantów, może spowodować znak kształtowania, zostanie utracone. Zamiast tego należy użyć odpowiedniego języka klawiatury do wprowadzania tekstu.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Aby poprawnie wyświetlić znaki, które nie są uwzględnione w bieżącej stronie kodowej

1.  Kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania**, a następnie otwórz **Opcje regionalne i językowe** (lub **Region** w [!INCLUDE[win8](../includes/win8-md.md)]).

    > [!NOTE]
    >  Musi być administratorem na komputerze, wykonaj następujące kroki.

2.  Kliknij przycisk **zaawansowane** kartę.

3.  W **wybierz język, aby dopasować wersję językową programy innego niż Unicode, którego chcesz użyć** listy, wybierz język, którego obecnie używasz.

4.  Kliknij przycisk **OK**.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Zmiana języka w tekst interfejsu użytkownika w programie Visual Studio
 Podczas instalowania wielu wersji językowych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tym samym komputerze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu użytkownika, wartość domyślna to **taki sam jak Microsoft Windows**. To ustawienie wskazuje, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wyświetli tekst interfejsu użytkownika w języku, który jest określony jako język wyświetlania systemu operacyjnego.

> [!NOTE]
>  Jeśli program Visual Studio jest skonfigurowany do używania **taki sam jak Microsoft Windows**i dopasowywania pakiet językowy programu Visual Studio nie jest zainstalowany, program Visual Studio będzie używać języka pierwszej instalacji programu Visual Studio.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Aby ustawić język, który jest używany tekst interfejsu użytkownika w programie Visual Studio

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. W **opcje** okna dialogowego rozwiń **środowiska** a następnie kliknij przycisk **ustawienia międzynarodowe**.

3. W **języka** , wybierz język, w którym powinna zostać wyświetlona tekst interfejsu użytkownika w środowisku programistycznym.

    Aby tekst interfejsu użytkownika w zgodne środowisko IDE języka wyświetlania systemu operacyjnego, ustawienie, zaznacz **taki sam jak Microsoft Windows**.

   Można również użyć polecenia devenv Aby ustawić język, który służy do interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Zobacz też
 [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../ide/reference/international-settings-environment-options-dialog-box.md)