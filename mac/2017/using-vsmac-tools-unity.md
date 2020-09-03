---
title: Korzystanie z narzędzi Visual Studio dla komputerów Mac dla aparatu Unity
description: W tym przewodniku opisano sposób użycia rozszerzenia Visual Studio dla komputerów Mac Tools for Unity
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315320"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Korzystanie z narzędzi Visual Studio dla komputerów Mac dla aparatu Unity

W tej sekcji dowiesz się, jak używać narzędzi Visual Studio dla komputerów Mac dla funkcji integracji i produktywności aparatu Unity oraz jak używać debugera Visual Studio dla komputerów Mac do tworzenia aplikacji dla środowiska Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otwieranie skryptów aparatu Unity w Visual Studio dla komputerów Mac

Gdy Visual Studio dla komputerów Mac jest [ustawiony jako zewnętrzny edytor skryptów dla aparatu Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otwarcie dowolnego skryptu z edytora Unity spowoduje automatyczne uruchomienie lub przełączenie do Visual Studio dla komputerów Mac, z otwartym wybranym skryptem.

Alternatywnie można otworzyć Visual Studio dla komputerów Mac bez otwartego skryptu w edytorze źródła, wybierając pozycję **Otwórz projekt C#** z menu **zasoby** w aparacie Unity.

![Otwórz projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity

Visual Studio dla komputerów Mac Tools for Unity zawiera skrót do uzyskiwania dostępu do dokumentacji interfejsu API aparatu Unity. Aby uzyskać dostęp do dokumentacji interfejsu API aparatu Unity z programu Visual Studio dla komputerów Mac, umieść kursor na interfejsie API Unity, którego chcesz się dowiedzieć, i naciśnij pozycję **⌘ Command + '**.

## <a name="intellisense-for-unity-messages"></a>Funkcja IntelliSense dla komunikatów Unity
Aparat Unity emituje komunikaty do skryptów bezskryptowych, co umożliwia deweloperom pisanie kodu, który reaguje na wiadomości, takie jak OnMouseDown, funkcja ontriggerenter itp. Ponieważ nie są to metody wirtualne w podstawowej klasie zachowań, niektóre środowisk IDE, takie jak narzędzie MonoDevelop, nie mają funkcji uzupełniania kodu dla komunikatów aparatu Unity.

Jednak narzędzia Visual Studio dla komputerów Mac dla aparatu Unity rozszerzają funkcjonalność funkcji IntelliSense na komunikaty aparatu Unity. Ułatwia to zaimplementowanie komunikatów Unity w skryptach o niedziałaniu i ułatwia naukę interfejsu API aparatu Unity. Aby używać funkcji IntelliSense dla komunikatów Unity:

1. Umieść kursor w nowym wierszu wewnątrz treści klasy, która pochodzi od charakteru.

2. Rozpocznij wpisywanie nazwy komunikatu aparatu Unity, na przykład `OnTriggerEnter` .

3. Po wpisaniu liter "**ONT**" zostanie wyświetlona lista sugestii IntelliSense.

   ![Korzystanie z IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Wybór na liście można zmienić na trzy sposoby:

   * Za pomocą klawiszy strzałek w **górę** i **w dół** .

   * Klikając przyciskiem myszy na żądanym elemencie.

   * Kontynuując wpisywanie nazwy żądanego elementu.

5. Technologia IntelliSense może wstawić wybrany komunikat Unity, w tym wszelkie niezbędne parametry:

   * Naciskając klawisz **Tab**.

   * Naciskając klawisz **Return**.

   * Przez dwukrotne kliknięcie wybranego elementu.

   ![Wstawianie komunikatu aparatu Unity z funkcji IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Dodawanie nowych plików i folderów aparatu Unity

Mimo że zawsze możesz dodawać nowe pliki do projektu Unity w edytorze Unity, Visual Studio dla komputerów Mac umożliwia łatwe tworzenie nowych skryptów aparatu Unity, programów do cieniowania i folderów z poziomu programu Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Dodaj nowy skrypt o niedziałaniu języka C#

Aby dodać nowy skrypt w języku C#, **kliknij prawym przyciskiem myszy folder Assets** lub jeden z jego podkatalogów w konsoli rozwiązania i wybierz polecenie **Dodaj > nowe**działanie.

![Dodaj nowe jednozachowanie](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Dodawanie nowego modułu cieniującego środowiska Unity

Aby dodać nowy program do cieniowania środowiska Unity, **kliknij prawym przyciskiem myszy folder Assets** lub podkatalog w konsoli rozwiązania i wybierz polecenie **Dodaj > nowy program do cieniowania**.

### <a name="add-a-new-folder"></a>Dodaj nowy folder

Aby dodać nowy folder, **kliknij prawym przyciskiem myszy folder Assets** lub podkatalog w konsoli rozwiązania i wybierz polecenie **Dodaj > nowy folder**.

Te dodatki są odzwierciedlone w oknie projektu edytora aparatu Unity.

### <a name="to-rename-a-file-or-folder"></a>Aby zmienić nazwę pliku lub folderu
**kliknij prawym przyciskiem myszy** element, aby zmienić jego nazwę w konsoli rozwiązania i wybierz polecenie **Zmień nazwę..**..

> [!NOTE]
> Jeśli masz nowy projekt środowiska Unity bez skryptów, a folder zasobów nie jest wyświetlany w konsoli rozwiązania w Visual Studio dla komputerów Mac, Dodaj początkowy skrypt języka C# z poziomu edytora aparatu Unity.

## <a name="unity-debugging"></a>Debugowanie aparatu Unity

Projekty Unity mogą być debugowane przy użyciu Visual Studio dla komputerów Mac.

### <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie:

1. Połącz program Visual Studio z aparatem Unity, klikając przycisk **Odtwórz** , lub wpisz **polecenie + Return**lub **F5**.

   ![Kliknij pozycję Odtwórz w programie Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Przejdź do aparatu Unity i kliknij przycisk **Odtwórz** , aby uruchomić grę w edytorze.

   ![Kliknij pozycję Odtwórz w środowisku Unity](media/using-vsmac-tools-unity-image6.png)

3. Gdy gra jest uruchomiona w edytorze aparatu Unity podczas połączenia z programem Visual Studio, wszystkie napotkane punkty przerwania spowodują wstrzymanie wykonywania gry i wyświetlenie wiersza kodu, w którym gra osiągnęła punkt przerwania w Visual Studio dla komputerów Mac.

### <a name="stop-debugging"></a>Zatrzymaj debugowanie

Aby zatrzymać debugowanie:

1. Kliknij przycisk **Zatrzymaj** w Visual Studio dla komputerów Mac lub naciśnij klawisze **Shift + Command + Return**.

   ![Kliknij przycisk Zatrzymaj w programie Visual Studio](media/using-vsmac-tools-unity-image7.png)

Aby dowiedzieć się więcej na temat debugowania w Visual Studio dla komputerów Mac, zobacz [Korzystanie z debugera](debugging.md).
