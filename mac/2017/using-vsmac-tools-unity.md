---
title: Używanie programu Visual Studio dla komputerów Mac Tools for Unity
description: Ten przewodnik opisuje jak używać programu Visual Studio dla komputerów Mac Tools for Unity rozszerzenia
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408541"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Używanie programu Visual Studio dla komputerów Mac Tools for Unity

W tej sekcji dowiesz się, jak używać programu Visual Studio dla komputerów Mac Tools do integracji firmy Unity i funkcji zwiększających wydajność i jak używać programu Visual Studio dla komputerów Mac debugera do tworzenia gier Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otwieranie skryptów Unity w programie Visual Studio dla komputerów Mac

Gdy Visual Studio dla komputerów Mac jest [ustawiony jako zewnętrzny edytor skryptów dla aparatu Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otwarcie dowolnego skryptu z edytora Unity spowoduje automatyczne uruchomienie lub przełączenie do Visual Studio dla komputerów Mac, z otwartym wybranym skryptem.

Alternatywnie można otworzyć Visual Studio dla komputerów Mac bez otwartego skryptu w edytorze źródła, wybierając pozycję  **C# Otwórz projekt** z menu **zasoby** w aparacie Unity.

![Otwórz projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity

Visual Studio dla komputerów Mac Tools for Unity zawiera skrót do uzyskiwania dostępu do dokumentacji interfejsu API aparatu Unity. Aby uzyskać dostęp do dokumentacji interfejsu API aparatu Unity z programu Visual Studio dla komputerów Mac, umieść kursor na interfejsie API Unity, którego chcesz się dowiedzieć, i naciśnij pozycję **⌘ Command + '** .

## <a name="intellisense-for-unity-messages"></a>Funkcja IntelliSense dla komunikatów Unity
Aparat Unity emituje komunikaty do skryptów bezskryptowych, co umożliwia deweloperom pisanie kodu, który reaguje na wiadomości, takie jak OnMouseDown, funkcja ontriggerenter itp. Ponieważ nie są to metody wirtualne w podstawowej klasie zachowań, niektóre środowisk IDE, takie jak narzędzie MonoDevelop, nie mają funkcji uzupełniania kodu dla komunikatów aparatu Unity.

Jednak program Visual Studio dla komputerów Mac Tools for Unity rozszerza jej funkcji IntelliSense, aby komunikaty aparatu Unity. Łatwo Implementuj komunikaty aparatu Unity w skryptach obiekt MonoBehaviour i pomaga nauki interfejsu API aparatu Unity. Aby użyć funkcji IntelliSense dla komunikatów Unity:

1. Umieść kursor w nowym wierszu w treści klasy, która jest pochodną obiekt MonoBehaviour.

2. Rozpocznij wpisywanie nazwy komunikatu aparatu Unity, takiej jak `OnTriggerEnter`.

3. Po wpisaniu liter "**ONT**" zostanie wyświetlona lista sugestii IntelliSense.

   ![Korzystanie z IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Wybór na liście, można zmienić na trzy sposoby:

   * Za pomocą klawiszy strzałek w **górę** i **w dół** .

   * Przez kliknięcie myszą do żądanego elementu.

   * Kontynuując wpisz nazwę żądanego elementu.

5. Technologia IntelliSense można wstawić wybrane wiadomości Unity, w tym wszelkie niezbędne parametry:

   * Naciskając klawisz **Tab**.

   * Naciskając klawisz **Return**.

   * Klikając wybrany element.

   ![Wstaw komunikatów aparatu Unity z technologii IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Dodawanie nowych plików Unity i folderów

Podczas gdy można zawsze dodawaj nowe pliki do projektu środowiska Unity w programie Unity editor, Visual Studio for Mac umożliwia łatwe tworzenie nowych skrypty Unity, programów do cieniowania i folderów z poziomu programu Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Dodaj nowy skrypt języka C# obiekt MonoBehaviour

Aby dodać nowy C# skrypt o nieprawidłowej obzachowań, **kliknij prawym przyciskiem myszy folder Assets** lub jeden z jego podkatalogów w konsoli rozwiązania i wybierz polecenie **Dodaj > nowe**działanie.

![Dodaj nowy element MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Dodaj nowy element shader aparatu Unity

Aby dodać nowy program do cieniowania środowiska Unity, **kliknij prawym przyciskiem myszy folder Assets** lub podkatalog w konsoli rozwiązania i wybierz polecenie **Dodaj > nowy program do cieniowania**.

### <a name="add-a-new-folder"></a>Dodaj nowy folder

Aby dodać nowy folder, **kliknij prawym przyciskiem myszy folder Assets** lub podkatalog w konsoli rozwiązania i wybierz polecenie **Dodaj > nowy folder**.

Te dodatki są uwzględniane w oknie projektu programu Unity editor.

### <a name="to-rename-a-file-or-folder"></a>Aby zmienić nazwę pliku lub folderu
**kliknij prawym przyciskiem myszy** element, aby zmienić jego nazwę w konsoli rozwiązania i wybierz polecenie **Zmień nazwę..** ..

> [!NOTE]
> Jeśli masz nowy projekt środowiska Unity za pomocą skryptów nie i folder zasobów nie jest wyświetlany w konsoli rozwiązania w programie Visual Studio dla komputerów Mac, należy dodać początkowej skrypt języka C# z w ramach programu Unity editor.

## <a name="unity-debugging"></a>Profilowanie aparatu Unity

Projekty Unity można debugować za pomocą programu Visual Studio dla komputerów Mac.

### <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie:

1. Połącz program Visual Studio z aparatem Unity, klikając przycisk **Odtwórz** , lub wpisz **polecenie + Return**lub **F5**.

   ![Kliknij przycisk odtwarzania w programie Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Przejdź do aparatu Unity i kliknij przycisk **Odtwórz** , aby uruchomić grę w edytorze.

   ![Kliknij przycisk Play na platformie Unity](media/using-vsmac-tools-unity-image6.png)

3. Uruchamiając gry w Edytor platformy Unity podczas połączenia z programu Visual Studio, wszelkie punkty przerwania, napotkała spowoduje wstrzymać wykonanie w gry i przywołać wiersza kodu, w którym gry trafiony punkt przerwania w programie Visual Studio dla komputerów Mac.

### <a name="stop-debugging"></a>Zatrzymaj debugowanie

Aby zatrzymać debugowanie:

1. Kliknij przycisk **Zatrzymaj** w Visual Studio dla komputerów Mac lub naciśnij klawisze **Shift + Command + Return**.

   ![Kliknij przycisk Zatrzymaj w programie Visual Studio](media/using-vsmac-tools-unity-image7.png)

Aby dowiedzieć się więcej na temat debugowania w Visual Studio dla komputerów Mac, zobacz [Korzystanie z debugera](debugging.md).
