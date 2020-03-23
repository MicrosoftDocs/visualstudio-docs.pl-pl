---
title: Visual Studio dla komputerów Mac dla użytkowników systemu Windows
description: Wprowadzenie funkcji ułatwień dostępu w programie Visual Studio dla komputerów Mac i sposobu ich włączenia.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984261"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio dla komputerów Mac dla użytkowników systemu Windows

Migracja z jednego systemu operacyjnego do drugiego może być zniechęcająca. Często występują subtelne różnice w aplikacjach między platformami, od interfejsu użytkownika do kategoryzacji elementów menu. Użytkownicy będą mieli również krzywą uczenia się aklimatyzacji do interfejsu użytkownika nowego systemu operacyjnego. W tym miejscu dowiesz się najbardziej typowych różnic między programem Visual Studio dla komputerów Mac a programem Visual Studio dla systemu Windows. Dowiesz się również kilku różnych konwencji między systemami macOS i Windows.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Jako deweloperzy, wielu z was będzie przyzwyczajony do korzystania z klawiatury do zadań i nawigacji. Niektóre klawisze na klawiaturze są wspólne dla komputerów Mac i Windows. Możesz być wybaczony za myślenie, że działania klawiatury, takie jak kopiowanie i wklejanie, używają tych samych kombinacji klawiszy. Nie zawsze tak jest. Na szczęście można zmienić powiązania klucza w programie Visual Studio dla komputerów Mac, aby ściśle odpowiadać powiązań programu Visual Studio w systemie Windows.

Przy pierwszym uruchomieniu programu Visual Studio dla komputerów Mac zostanie ![wyświetlene okno wyboru skrótów klawiaturowych: okno powiązania klawiszy](media/ide-tour-2019-keyboard-shortcut.png)

Jeśli chcesz później zmienić powiązania klawiszy, możesz znaleźć to ![ustawienie w preferencjach: Preferencje powiązań klawiszy](media/customizing-the-ide-image10a.png)

Należy pamiętać, że system macOS używa różnych skrótów systemowych do systemu Windows. Zmiana preferencji wiązania kluczy umożliwia używanie znanych skrótów systemu Windows w programie Visual Studio dla komputerów Mac. Jednak w innych obszarach systemu macOS musisz znać skróty systemu macOS.

Klawisz modyfikatora polecenia systemu macOS (♡) może często zastąpić klawisz Control w systemie Windows. Oto kilka przykładów i inne często używane skróty:

|Zadanie                   |Skrót systemu Windows         |Skrót do systemu macOS      |
|-----------------------|-------------------------|--------------------|
|Copy                   |`Ctrl + C`               |`⌘ + C`             |
|Wklej                  |`Ctrl + V`               |`⌘ + V`             |
|Wytnij                    |`Ctrl + X`               |`⌘ + X`             |
|Cofanie                   |`Ctrl + Z`               |`⌘ + Z`             |
|Ponów                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Usuwanie prawa kursora |`Delete`                 |`fn + Backspace`    |
|Usuwanie wyrazu            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Pełną listę skrótów do systemu macOS można znaleźć w [witrynie wsparcia Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menu

Menu w systemie macOS są zorganizowane inaczej niż menu w systemie Windows. Visual Studio dla komputerów Mac nie jest wyjątkiem. Niektóre z najpopularniejszych opcji menu można znaleźć tutaj:

|Zadanie                   |Visual Studio (Windows)                                              |Visual Studio dla komputerów Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferencje (opcje)  |Narzędzia > opcje...                                                   |Preferencje > programu Visual Studio...       |
|Rozszerzenia             |Rozszerzenia > zarządzanie rozszerzeniami                                       |Rozszerzenia > programu Visual Studio...        |
|Układy                |> okna Zastosuj > układu okna [Wybierz układ]                       |Wyświetl > [Wybierz układ]               |
|Aktualizacje                |Pomoc > sprawdzanie dostępności aktualizacji                                             |Visual Studio > Sprawdź dostępność aktualizacji... |
|Menedżer pakietów NuGet  |Narzędzia > Menedżer pakietów NuGet > zarządzanie pakietami nuget lub rozwiązaniem... |> projektu zarządzaj pakietami NuGet...   |
|Podkładki / Windows         |Wyświetl > [Wybierz pad / okno]                                         |Wyświetl > pady > [Wybierz podkładkę / okno]  |
|Znajdź narzędzia             |Edytuj > Znajdź i zamień > [Wybierz narzędzie]                              |Wyszukiwanie > [Wybierz narzędzie]               |
|Informacje o programie Visual Studio    |> pomocy dotyczące programu Microsoft Visual Studio                                 |Program Visual Studio > informacje o programie Visual Studio  

> [!NOTE]
> Przegląd najczęściej spotykanych funkcji w programie Visual Studio dla komputerów Mac można znaleźć w [przewodniku IDE Tour](ide-tour.md)