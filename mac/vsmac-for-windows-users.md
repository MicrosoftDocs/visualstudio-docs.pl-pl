---
title: Visual Studio dla komputerów Mac dla użytkowników systemu Windows
description: Wprowadzenie funkcji ułatwień dostępu w Visual Studio dla komputerów Mac i sposobach ich włączenia.
author: alclark
ms.author: alcl
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 3306cdec93b501ad2006bbee2ceca3bf42514fe9
ms.sourcegitcommit: 7739f36507b4762eea83c692102bdc5188460f28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71314487"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio dla komputerów Mac dla użytkowników systemu Windows

Migracja z jednego systemu operacyjnego do innego może być zniechęcające. Często istnieją drobne różnice między aplikacjami wieloplatformowymi, od interfejsu użytkownika do kategoryzacji elementów menu. Użytkownicy będą również mieć krzywą szkoleniową acclimatizing do interfejsu użytkownika nowego systemu operacyjnego. W tym miejscu przedstawiono najczęstsze różnice między Visual Studio dla komputerów Mac i Visual Studio dla systemu Windows. Poznasz również kilka różnych konwencji między macOS i Windows.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Jako Deweloperzy, wiele z nich zostanie pozyskanych przy użyciu klawiatury do zadań i nawigacji. Niektóre klucze na klawiaturze są wspólne między komputerami Mac i komputerów z systemem Windows. Można Forgiven na przykład, że akcje klawiatury, takie jak kopiowanie i wklejanie, używają tych samych kombinacji klawiszy. Nie zawsze jest to przypadek. Na szczęście można zmienić kluczowe powiązania w Visual Studio dla komputerów Mac, aby dokładnie dopasować je do programu Visual Studio w systemie Windows.

Przy pierwszym uruchomieniu Visual Studio dla komputerów Mac zobaczysz okno wyboru skrótów klawiaturowych: ![Okno powiązań klucza](media/ide-tour-2019-keyboard-shortcut.png)

Jeśli chcesz później zmienić powiązania klawiszy, możesz znaleźć ustawienie w preferencjach: ![Preferencje kluczowych powiązań](media/customizing-the-ide-image10a.png)

Należy pamiętać, że macOS używa różnych skrótów do systemu Windows. Zmiana preferencji powiązania klucza umożliwi korzystanie ze znanych skrótów systemu Windows w Visual Studio dla komputerów Mac. Jednak w innych obszarach macOS trzeba znać skróty macOS.

Klucz modyfikatora macOS Command (⌘) może zazwyczaj zastąpić klucz kontrolny w systemie Windows. Oto kilka przykładów i inne często używane skróty:

|Zadanie                   |Skrót systemu Windows         |Skrót macOS      |
|-----------------------|-------------------------|--------------------|
|Kopiuj                   |`Ctrl + C`               |`⌘ + C`             |
|Wklej                  |`Ctrl + V`               |`⌘ + V`             |
|Wytnij                    |`Ctrl + X`               |`⌘ + X`             |
|Cofnij                   |`Ctrl + Z`               |`⌘ + Z`             |
|Wykonaj ponownie                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Usuń prawo od kursora |`Delete`                 |`fn + Backspace`    |
|Usuń słowo            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Kompleksową listę skrótów macOS można znaleźć w [witrynie sieci Web pomocy technicznej firmy Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menu

Menu w macOS są zorganizowane inaczej niż w przypadku menu w systemie Windows. Visual Studio dla komputerów Mac nie jest wyjątkiem. Niektóre z najpopularniejszych opcji menu można znaleźć tutaj:

|Zadanie                   |Visual Studio (Windows)                                              |Visual Studio for Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferencje (Opcje)  |Narzędzia > Opcje...                                                   |Preferencje > programu Visual Studio...       |
|Rozszerzenia             |Rozszerzenia > Zarządzanie rozszerzeniami                                       |Rozszerzenia programu Visual Studio >...        |
|Układy                |Okno > stosowanie układu okna > [Wybierz układ]                       |Wyświetl > [Wybierz układ]               |
|Aktualizacje                |Pomoc > Sprawdzanie dostępności aktualizacji                                             |Program Visual Studio > Sprawdzanie dostępności aktualizacji... |
|Menedżer pakietów NuGet  |Narzędzia > Menedżera pakietów NuGet > zarządzania pakietami lub rozwiązaniem NuGet... |> Projektu Zarządzaj pakietami NuGet...   |
|Konsole/okna         |Wyświetl > [Wybierz konsolę/okno]                                         |Wyświetl > konsole > [Wybierz konsolę/okno]  |
|Znajdź narzędzia             |Edytowanie > Znajdowanie i zastępowanie > [Wybierz narzędzie]                              |> Wyszukiwania [Wybierz narzędzie]               |
|Informacje o programie Visual Studio    |Pomoc > na temat Microsoft Visual Studio                                 |Program Visual Studio > o programie Visual Studio  

> [!NOTE]
> Przegląd typowych funkcji dostępnych w programie Visual Studio dla komputerów Mac można znaleźć w [przewodniku IDE](ide-tour.md)