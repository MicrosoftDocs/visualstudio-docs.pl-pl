---
title: Zarządzanie właściwościami projektów i rozwiązań
description: W tym artykule opisano sposób zarządzania właściwościami projektów i rozwiązań w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692880"
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

## <a name="project-options"></a>Opcje projektu

Opcje projektu są specyficzne dla każdego projektu i wpływają na sposób pisania, konfigurowania i uruchamiania projektu. To kontrastuje z visual studio preferencji dla komputerów Mac (który ustawia opcje specyficzne dla użytkownika) i opcje rozwiązania (które ustawiają opcje dla całego rozwiązania). Opcje projektu są przechowywane w pliku projektu (csproj), dzięki czemu inni deweloperzy mogą poprawnie skompilować i uruchomić projekt. Posiadanie określonych opcji projektu umożliwia wielu deweloperom pracę nad tym samym dokumentem bez uszczerbku dla formatowania pliku.

Aby otworzyć opcje programu Project w programie Visual Studio dla komputerów Mac, kliknij dwukrotnie nazwę projektu lub kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz pozycję **Opcje:**

![Opcja w menu kontekstowym](media/projects-and-solutions-image2.png)

Edytowalne opcje obejmują opcje tworzenia, uruchamiania i ustawiania kodu źródłowego i kontroli wersji.

Opcje projektu są podzielone na pięć różnych kategorii:

* **Ogólne** — informacje o projekcie, takie jak Nazwa, Opis i Domyślny obszar nazw są ustawione w tym miejscu, wraz z lokalizacją projektu.
* **Kompilacja** — umożliwia deweloperom ustawianie lub zmienianie profili PCL dla przenośnych bibliotek klas. Umożliwia również ustawienie niestandardowych poleceń, konfiguracji, opcji kompilatora. W tym miejscu można również ustawić ścieżkę wyjściową i nazwę zestawu.
* **Uruchom** — umożliwia tworzenie niestandardowych konfiguracji uruchamiania na podstawie projektu.
* **Kod źródłowy** — umożliwia sterowanie formatowaniem wielu różnych typów plików i konwencji nazewnictwa. W tym miejscu można również ustawić zasady nazewnictwa i domyślne style nagłówków.
* **Kontrola wersji** — umożliwia edytowanie stylu komunikatu zatwierdzania podczas korzystania z kontroli wersji z projektem.

Każdy projekt może zawierać określone opcje projektu, w zależności od platformy. Na przykład projekt Xamarin.Android, podobnie jak ten zilustrowany na poniższej ilustracji, ma opcje odnoszące się do kompilacji systemu Android (takie jak opcje konsolidatora) i aplikacji (takie jak uprawnienia):

![Opcje projektu systemu Android](media/projects-and-solutions-image5.png)

Xamarin.iOS ma opcje związane z podpisywaniem pakietu — takie jak wymagany profil inicjowania obsługi administracyjnej do użycia:

![Opcje projektu systemu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opcje rozwiązania

Opcje rozwiązania są podobne do opcji projektu, ale obejmują zakres całych rozwiązań. Umożliwiają one ustawienie informacji o autorze, ustawienia kompilacji, style formatowania kodu i kontrolę wersji, a także umożliwiają przypisanie projektu startowego w rozwiązaniu.  Dostęp do okna dialogowego Opcje rozwiązania można uzyskać z pozycji menu **> Opcje rozwiązania projektu,** z pozycji menu kontekstowego **Opcje** na panelu rozwiązania lub po dwukrotnym kliknięciu przycisku Rozwiązanie w panelu rozwiązania:

![Opcje rozwiązania](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Zobacz też

* [Zarządzanie właściwościami projektu i rozwiązania (Visual Studio w systemie Windows)](/visualstudio/ide/managing-project-and-solution-properties)