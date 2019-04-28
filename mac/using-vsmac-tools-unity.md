---
title: Używanie programu Visual Studio dla komputerów Mac Tools for Unity
description: Ten przewodnik opisuje jak używać programu Visual Studio dla komputerów Mac Tools for Unity rozszerzenia
author: therealjohn
ms.author: johmil
ms.date: 04/02/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 56050de063dcbc86bfa469ee9f466a8e87bba973
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966030"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Używanie programu Visual Studio dla komputerów Mac Tools for Unity

W tej sekcji dowiesz się, jak używać programu Visual Studio dla komputerów Mac Tools do integracji firmy Unity i funkcji zwiększających wydajność i jak używać programu Visual Studio dla komputerów Mac debugera do tworzenia gier Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otwieranie skryptów Unity w programie Visual Studio dla komputerów Mac

Gdy program Visual Studio dla komputerów Mac [edytorem skryptu zewnętrznego dla aparatu Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), Otwieranie dowolnego skryptu za pomocą programu Unity editor spowoduje automatyczne uruchomienie lub Otwórz przełącznika w programie Visual Studio dla komputerów Mac, za pomocą wybranego skryptu.

Alternatywnie program Visual Studio for Mac może być otwierany przez skrypt nie jest otwarty w edytorze źródła, wybierając **Otwórz projekt C#** z **zasoby** menu na platformie Unity.

![Otwórz projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity

Visual Studio dla komputerów Mac Tools for Unity zawiera skrót do uzyskiwania dostępu do dokumentacji interfejsu API aparatu Unity. Aby uzyskać dostęp do dokumentacji interfejsu API aparatu Unity w programie Visual Studio dla komputerów Mac, umieść kursor nad interfejsu API aparatu Unity, aby poznać i naciśnij klawisz **⌘ polecenia + "**.

## <a name="intellisense-for-unity-messages"></a>Funkcja IntelliSense dla komunikatów Unity
Aparat Unity emituje komunikaty do obiekt MonoBehaviour skryptów, dzięki czemu deweloperzy mogą pisać kod, który reaguje na komunikaty, takie jak OnMouseDown, OnTriggerEnter itp. Ponieważ nie są to wirtualne metody w klasie bazowej obiekt MonoBehaviour, niektórych środowisk IDE, takie jak narzędzia MonoDevelop nie mają funkcji uzupełniania kodu dla komunikatów Unity.

Jednak program Visual Studio dla komputerów Mac Tools for Unity rozszerza jej funkcji IntelliSense, aby komunikaty aparatu Unity. Łatwo Implementuj komunikaty aparatu Unity w skryptach obiekt MonoBehaviour i pomaga nauki interfejsu API aparatu Unity. Aby użyć funkcji IntelliSense dla komunikatów Unity:

1. Umieść kursor w nowym wierszu w treści klasy, która jest pochodną obiekt MonoBehaviour.

2. Rozpocznij wpisywanie nazwy Unity komunikatów, takie jak `OnTriggerEnter`.

3. Gdy litery "**ont**" został wpisany, zostanie wyświetlona lista sugestie funkcji IntelliSense.

   ![Korzystanie z IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Wybór na liście, można zmienić na trzy sposoby:

   * Za pomocą **się** i **dół** klawiszy strzałek.

   * Przez kliknięcie myszą do żądanego elementu.

   * Kontynuując wpisz nazwę żądanego elementu.

5. Technologia IntelliSense można wstawić wybrane wiadomości Unity, w tym wszelkie niezbędne parametry:

   * Naciskając **kartę**.

   * Naciskając **zwracają**.

   * Klikając wybrany element.

   ![Wstaw komunikatów aparatu Unity z technologii IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Dodawanie nowych plików Unity i folderów

Podczas gdy można zawsze dodawaj nowe pliki do projektu środowiska Unity w programie Unity editor, Visual Studio for Mac umożliwia łatwe tworzenie nowych skrypty Unity, programów do cieniowania i folderów z poziomu programu Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Dodaj nowy skrypt języka C# obiekt MonoBehaviour

Aby dodać nowy skrypt języka C# obiekt MonoBehaviour **kliknij prawym przyciskiem myszy w folderze Zasoby** lub jeden z jego podkatalogów w konsoli rozwiązania i wybierz **Dodaj > Nowy element MonoBehaviour**.

![Dodaj nowy element MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Dodaj nowy element shader aparatu Unity

Aby dodać nowy moduł cieniujący Unity **kliknij prawym przyciskiem myszy w folderze Zasoby** lub podkatalogu w konsoli rozwiązania i wybierz **Dodaj > Nowy program do cieniowania**.

### <a name="add-a-new-folder"></a>Dodaj nowy folder

Aby dodać nowy folder **kliknij prawym przyciskiem myszy w folderze Zasoby** lub podkatalogu w konsoli rozwiązania i wybierz **Dodaj > Nowy Folder**.

Te dodatki są uwzględniane w oknie projektu programu Unity editor.

### <a name="to-rename-a-file-or-folder"></a>Aby zmienić nazwę pliku lub folderu
**Kliknij prawym przyciskiem myszy** na elemencie, aby zmienić nazwę w rozwiązaniu do konsoli, a następnie wybierz pozycję **zmiany nazwy...** .

> [!NOTE]
> Jeśli masz nowy projekt środowiska Unity za pomocą skryptów nie i folder zasobów nie jest wyświetlany w konsoli rozwiązania w programie Visual Studio dla komputerów Mac, należy dodać początkowej skrypt języka C# z w ramach programu Unity editor.

## <a name="unity-debugging"></a>Profilowanie aparatu Unity

Projekty Unity można debugować za pomocą programu Visual Studio dla komputerów Mac.

### <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie:

1. Łączenie programu Visual Studio do aparatu Unity, klikając **Odtwórz** przycisku lub typ **polecenia + Return**, lub **F5**.

   ![Kliknij przycisk odtwarzania w programie Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Przełącz do aparatu Unity i kliknij przycisk **Odtwórz** przycisk, aby uruchomić grę w edytorze.

   ![Kliknij przycisk Play na platformie Unity](media/using-vsmac-tools-unity-image6.png)

3. Uruchamiając gry w Edytor platformy Unity podczas połączenia z programu Visual Studio, wszelkie punkty przerwania, napotkała spowoduje wstrzymać wykonanie w gry i przywołać wiersza kodu, w którym gry trafiony punkt przerwania w programie Visual Studio dla komputerów Mac.

### <a name="start-debugging-in-a-single-step"></a>Rozpocznij debugowanie w jednym kroku

Począwszy od debugowania i odtwarzanie programu Unity editor zakończeniem w jednym kroku bezpośrednio z programu Visual Studio dla komputerów Mac, wybierając **Dołącz do aparatu Unity i Odtwórz** konfiguracji.

![Wybierz opcję Dołącz do aparatu Unity i Odtwórz](media/using-vsmac-tools-unity-image8.png)

### <a name="stop-debugging"></a>Zatrzymaj debugowanie

Aby zatrzymać debugowanie:

1. Kliknij przycisk **zatrzymać** przycisku w programie Visual Studio for Mac lub naciśnij **Shift + polecenia + Return**.

   ![Kliknij przycisk Zatrzymaj w programie Visual Studio](media/using-vsmac-tools-unity-image7.png)

> [!NOTE]
> Jeśli rozpoczęto debugowanie przy użyciu **Dołącz do aparatu Unity i Odtwórz** konfiguracji **zatrzymać** przycisku spowoduje również przerwanie aparatu Unity.

Aby dowiedzieć się więcej o debugowaniu w programie Visual Studio dla komputerów Mac, zobacz [za pomocą debugera](debugging.md).
