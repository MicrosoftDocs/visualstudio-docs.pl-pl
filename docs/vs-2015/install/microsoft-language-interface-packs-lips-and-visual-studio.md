---
title: Pakiety Microsoft Language Interface Pack (lip) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 503f97d1530f8d22184f42a2452046782a997c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814325"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Pakiety języka interfejsu użytkownika (LIP) firmy Microsoft a program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą pakietu Windows Language Pack (LIP) można zainstalować wersję językową systemu Windows, a następnie zainstalować różne pakiety językowe interfejsu użytkownika. Pakiety językowe interfejsu użytkownika zapewniają zlokalizowany interfejs użytkownika dla systemu operacyjnego. Na przykład można zainstalować pakiet języka japońskiego w wersji angielskiej systemu Windows, a następnie przełączyć język interfejsu użytkownika systemu Windows między językiem japońskim i angielskim. Korzystając z pakietów lip, można mieć wiele wersji językowych systemu Windows na jednym komputerze.

 Na komputerach, na których zainstalowano pakiety lip i wiele wersji językowych programu Visual Studio, zmiana ustawień języka wyświetlania systemu Windows ustawia zarówno system Windows, jak i program Visual Studio, gdy są zainstalowane odpowiednie pakiety językowe.

## <a name="limitations-of-multi-language-installations"></a>Ograniczenia instalacji wielojęzycznych
 W przypadku instalowania różnych wersji językowych programu Visual Studio na tym samym komputerze, można przełączać tylko języki między zgodnymi wersjami. Jeśli na przykład masz zainstalowaną angielską wersję Express Edition, zainstalowano Niemieckią wersję Express, a wersja Professional Edition, można przełączać tylko języki dla wersji Express, a nie dla wersji Professional.

 Program Visual Studio używa ujednoliconego pakietu językowego. Aby zainstalować więcej niż jedną wersję językową tych produktów, należy najpierw zainstalować pełen produkt językowy, a następnie zainstalować jeden lub więcej pakietów językowych.

> [!NOTE]
> Program Visual Studio nie obsługuje instalowania wielu wersji językowych produktu na tym samym komputerze. Po zainstalowaniu jednego pełnego produktu językowego należy dodać wersje językowe przy użyciu pakietów językowych. Można nadal instalować wiele pełnych produktów językowych wersji Express na tym samym komputerze.

### <a name="support-for-code-pages"></a>Obsługa stron kodowych
 Niektóre narzędzia Visual Studio nie wyświetlają poprawnie tekstu, gdy tekst zawiera znaki, które nie znajdują się na bieżącej stronie kodowej. Zamiast tego pojawiają się znaki zapytania lub tekst jest uszkodzony. Dotyczy to następujących narzędzi lub obszarów:

- Lokacje wdrożone przy użyciu protokołu FTP.

- Nazwy komputerów innych niż ASCII w niektórych kontrolkach.

- Narzędzia wiersza polecenia, które działają poza programem Visual Studio.

- Kreator migracji Visual Basic.

- Kontener testu kontrolki ActiveX.

- Przeglądarka obiektów OLE/COM.

- Narzędzie debugowania sieci Web dla interfejsu ISAPI.

- Projekty aplikacji MFC, które mają zawartość pomocy HTML.

- Interfejs użytkownika programu Visual SourceSafe/SCCI powraca do języka angielskiego, gdy jest niezgodna strona kodowa.

- Program Visual SourceSafe nie obsługuje nazw plików Unicode.

- Znaki zdefiniowane przez użytkownika (prywatna strefa use) nie mogą być używane jako tokeny/identyfikatory.

- Znaki łacińskie Extended-B nie mogą być wyświetlane w niektórych oknach narzędzi programu Visual Studio, gdy strona kodowa systemu Windows jest ustawiona na język wschodnioazjatycki.

- W przypadku tekstów zawierających znaki z wielu skryptów języka może być wyświetlany domyślny symbol dla niektórych znaków.

- Kopiowanie i wklejanie złożonych ciągów skryptu do wspólnych kontrolek może spowodować utratę kształtu znaków. Zamiast tego należy użyć odpowiedniej klawiatury języka do wprowadzania tekstu.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Aby poprawnie wyświetlić znaki, które nie znajdują się na bieżącej stronie kodowej

1. Kliknij przycisk **Start**, kliknij pozycję **Panel sterowania**, a następnie otwórz **Opcje regionalne i językowe** (lub **region** w programie [!INCLUDE[win8](../includes/win8-md.md)] ).

    > [!NOTE]
    > Aby wykonać te kroki, musisz być administratorem na komputerze.

2. Kliknij kartę **Zaawansowane**.

3. Z listy **Wybierz język, aby dopasować wersję językową programów innych niż Unicode, których chcesz użyć** , wybierz język, który jest aktualnie używany.

4. Kliknij przycisk **OK**.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Zmiana języka używanego dla tekstu interfejsu użytkownika w programie Visual Studio
 W przypadku instalowania wielu wersji językowych programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tym samym komputerze, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejs użytkownika jest domyślnie **taki sam jak Microsoft Windows**. To ustawienie wskazuje, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program będzie wyświetlał tekst interfejsu użytkownika w języku, który jest określony jako język wyświetlania systemu operacyjnego.

> [!NOTE]
> Jeśli program Visual Studio jest ustawiony do użycia **tak samo jak Microsoft Windows**, a nie zainstalowano zgodnego pakietu językowego programu Visual Studio, program Visual Studio użyje języka pierwszej instalacji programu Visual Studio.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Aby ustawić język używany dla tekstu interfejsu użytkownika w programie Visual Studio

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. W oknie dialogowym **Opcje** rozwiń węzeł **środowisko** , a następnie kliknij pozycję **Ustawienia międzynarodowe**.

3. Na liście **Język** wybierz język, w którym tekst interfejsu użytkownika powinien być wyświetlany w środowisku deweloperskim.

    Aby tekst interfejsu użytkownika w środowisku IDE odpowiadał ustawieniu języka wyświetlania systemu operacyjnego, wybierz **taki sam jak system Microsoft Windows**.

   Możesz również użyć polecenia devenv, aby ustawić język używany przez interfejs użytkownika. Aby uzyskać więcej informacji, zobacz [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Zobacz też
 [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../ide/reference/international-settings-environment-options-dialog-box.md)