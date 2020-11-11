---
title: Zarządzanie właściwościami projektów i rozwiązań
description: W tym artykule opisano sposób zarządzania właściwościami projektów i rozwiązań w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493000"
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

## <a name="project-options"></a>Opcje projektu

Opcje projektu są specyficzne dla każdego projektu i wpływają na sposób pisania, kompilowania i uruchamiania projektu. W przeciwieństwie do preferencji Visual Studio dla komputerów Mac, które są ustawieniami specyficznymi dla użytkownika, opcje projektu są przechowywane w pliku projektu (. csproj), tak aby inni deweloperzy mogli poprawnie kompilować i uruchamiać projekt. Posiadanie określonych opcji projektu pozwala wielu deweloperom na działanie tego samego dokumentu bez naruszania formatowania pliku.

Aby otworzyć Opcje projektu w Visual Studio dla komputerów Mac, kliknij dwukrotnie nazwę projektu lub kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz **Opcje** :

![Opcja w menu kontekstowym](media/projects-and-solutions-image2.png)

Opcje edytowalne obejmują opcje kompilowania, uruchamiania i ustawiania kodu źródłowego i kontroli wersji.

Opcje projektu są zorganizowane w pięć różnych kategorii:

* **Ogólne** — informacje o projekcie, takie jak nazwa, opis i domyślna przestrzeń nazw, są ustawiane w tym miejscu wraz z lokalizacją projektu.
* **Kompilacja** — służy do ustawiania lub zmieniania profilów PCL dla przenośnych bibliotek klas. Umożliwia również niestandardowe polecenia, konfiguracje, opcje kompilatora, które mają być ustawione. W tym miejscu można również ustawić ścieżkę wyjściową i nazwę zestawu.
* **Uruchom** — służy do tworzenia niestandardowych konfiguracji uruchamiania dla poszczególnych projektów.
* **Kod źródłowy** — kontroluje formatowanie wielu różnych typów plików i konwencji nazewnictwa. W tym miejscu możesz również ustawić zasady nazewnictwa i domyślne style nagłówków.
* **Kontrola wersji** — opcje, aby ustawić styl komunikatów zatwierdzania w przypadku używania kontroli wersji z projektem.

Każdy projekt może zawierać konkretne opcje projektu, w zależności od platformy. Na przykład projekt Xamarin. Android, podobny do przedstawionego na poniższej ilustracji, zawiera opcje dotyczące kompilacji systemu Android (takie jak Opcje konsolidatora) i aplikacji (na przykład uprawnienia):

![Opcje projektu dla systemu Android](media/projects-and-solutions-image5.png)

Platforma Xamarin. iOS zawiera opcje związane z podpisywaniem pakietu — na przykład wymaganym profilem aprowizacji:

![Opcje projektu systemu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opcje rozwiązania

Opcje rozwiązania są podobne do opcji projektu, ale obejmują zakres wszystkich rozwiązań. Umożliwiają one Ustawianie informacji o autorze, ustawień kompilacji, stylów formatowania kodu i kontroli wersji oraz umożliwiają przypisanie projektu startowego w rozwiązaniu.  Do okna dialogowego Opcje rozwiązania można uzyskać dostęp z elementu menu **Opcje rozwiązania projektu >** , z elementu menu kontekstowego **opcji** w rozwiązaniu w oknie rozwiązania lub klikając dwukrotnie rozwiązanie w oknie rozwiązania:

![Opcje rozwiązania](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Zobacz też

* [Zarządzanie właściwościami projektów i rozwiązań (Visual Studio w systemie Windows)](/visualstudio/ide/managing-project-and-solution-properties)