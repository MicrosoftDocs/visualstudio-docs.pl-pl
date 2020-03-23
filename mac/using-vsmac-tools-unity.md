---
title: Korzystanie z programu Visual Studio for Mac Tools for Unity
description: W tym przewodniku opisano sposób używania programu Visual Studio dla komputerów Mac Tools dla rozszerzenia Unity
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 4247e5cfb936d79c2b2bea5ac68a16164f0c0ef0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79303338"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Korzystanie z programu Visual Studio for Mac Tools for Unity

W tej sekcji dowiesz się, jak używać programu Visual Studio for Mac Tools dla funkcji integracji i produktywności unity oraz jak używać debugera programu Visual Studio dla komputerów Mac do tworzenia unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otwieranie skryptów Unity w programie Visual Studio dla komputerów Mac

Gdy program Visual Studio dla komputerów Mac zostanie [ustawiony jako zewnętrzny edytor skryptów dla unity,](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)otwarcie dowolnego skryptu z edytora Unity zostanie automatycznie uruchomione lub przełącze się do programu Visual Studio dla komputerów Mac z otwartym wybranym skryptem.

Alternatywnie visual studio dla **komputerów** Mac można otworzyć bez otwierania skryptu w edytorze źródłowym, wybierając **open C# Project** z menu Zasoby w Unity.

![Otwórz projekt W#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji unity

Visual Studio for Mac Tools for Unity zawiera skrót do uzyskiwania dostępu do dokumentacji interfejsu API Unity. Aby uzyskać dostęp do dokumentacji interfejsu API Unity z programu Visual Studio for Mac, umieść kursor za pomocą interfejsu API Unity, o który chcesz się dowiedzieć, i naciśnij **polecenie ♠ + .**

## <a name="intellisense-for-unity-messages"></a>Komunikaty IntelliSense for Unity
Aparat Unity emituje wiadomości do skryptów MonoBehaviour, umożliwiając deweloperom pisanie kodu, który reaguje na wiadomości, takie jak OnMouseDown, OnTriggerEnter itp. Ponieważ nie są to metody wirtualne w podstawowej klasie MonoBehaviour, niektóre środowiska IDE, takie jak MonoDevelop, nie mają funkcji uzupełniania kodu dla komunikatów Unity.

Jednak Visual Studio for Mac Tools for Unity rozszerza jego funkcji IntelliSense do komunikatów Unity. Ułatwia to implementowanie komunikatów Unity w skryptach MonoBehaviour i pomaga w nauce interfejsu API Unity. Aby użyć komunikatów IntelliSense for Unity:

1. Umieść kursor na nowej linii wewnątrz treści klasy, która wywodzi się z MonoBehaviour.

2. Zacznij wpisywać nazwę wiadomości Unity, `OnTriggerEnter`na przykład .

3. Po wpisaniu liter "**ont**" pojawi się lista sugestii IntelliSense.

   ![Korzystanie z IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Zaznaczenie na liście można zmienić na trzy sposoby:

   * Za pomocą klawiszy strzałek **w górę** i **w dół.**

   * Klikając myszką na żądany element.

   * Kontynuując wpisywanie nazwy żądanego elementu.

5. IntelliSense może wstawić wybrany komunikat Unity, łącznie z niezbędnymi parametrami:

   * Naciskając **klawisz Tab**.

   * Naciskając **przycisk Return**.

   * Klikając dwukrotnie wybrany element.

   ![Wstaw komunikat Unity z usługi IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Dodawanie nowych plików i folderów Unity

Chociaż zawsze można dodać nowe pliki do projektu Unity w edytorze Unity, Visual Studio dla komputerów Mac umożliwia łatwe tworzenie nowych skryptów Unity, modułów cieniujących, struktur, wyliczenia i folderów z poziomu programu Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Dodawanie nowego skryptu MonoBehaviour w języku C#

Aby dodać nowy skrypt MonoBehaviour w języku C#, **kliknij prawym przyciskiem myszy folder Zasoby** lub jeden z jego podkatalogów w konsoli rozwiązania i wybierz pozycję **Dodaj > Nowe monobekonuszt .**

![Dodaj nowe MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Dodawanie nowego modułu cieniującego Unity

Aby dodać nowy moduł cieniujący Unity, **kliknij prawym przyciskiem myszy folder Zasoby** lub podkatalog w konsoli Rozwiązania i wybierz polecenie Dodaj > nowy moduł **cieniujący**.

### <a name="add-a-new-folder"></a>Dodawanie nowego folderu

Aby dodać nowy folder, **kliknij prawym przyciskiem myszy folder Zasoby** lub podkatalog w konsoli Rozwiązanie i wybierz polecenie Dodaj > Nowy **folder**.

Te dodatki są odzwierciedlane w oknie projektu edytora Unity.

### <a name="to-rename-a-file-or-folder"></a>Aby zmienić nazwę pliku lub folderu
**kliknij prawym przyciskiem myszy** element, aby zmienić nazwę w konsoli rozwiązania i wybierz pozycję **Zmień nazwę...**.

> [!NOTE]
> Jeśli masz nowy projekt Unity bez skryptów i folder Zasoby nie jest wyświetlany w panelu rozwiązania w programie Visual Studio dla komputerów Mac, dodaj początkowy skrypt C# z poziomu edytora Unity.

## <a name="unity-debugging"></a>Debugowanie jedności

Projekty Unity można debugować za pomocą programu Visual Studio dla komputerów Mac.

### <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie:

1. Połącz program Visual Studio z unity, klikając przycisk **Odtwórz** lub wpisz **Polecenie + Powrót**lub **F5**.

   ![Kliknij przycisk Odtwórz w programie Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Przełącz się na Jedność i kliknij przycisk **Odtwórz,** aby uruchomić grę w edytorze.

   ![Kliknij przycisk Odtwórz w jedności](media/using-vsmac-tools-unity-image6.png)

3. Gdy gra jest uruchomiona w edytorze Unity podczas połączenia z programem Visual Studio, wszystkie punkty przerwania napotkane wstrzyma wykonanie gry i przywołać wiersz kodu, w którym gra trafić punkt przerwania w programie Visual Studio dla komputerów Mac.

### <a name="start-debugging-in-a-single-step"></a>Rozpoczynanie debugowania w jednym kroku

Uruchamianie debugowania i odtwarzania edytora Unity można wykonać w jednym kroku bezpośrednio z programu Visual Studio dla komputerów Mac, wybierając dołącz do unity i konfiguracji **Play.**

![Wybierz pozycję Dołącz do unity i play](media/using-vsmac-tools-unity-image8.png)

### <a name="stop-debugging"></a>Zatrzymywać debugowanie

Aby zatrzymać debugowanie:

1. Kliknij przycisk **Zatrzymaj** w programie Visual Studio dla komputerów Mac lub naciśnij **klawisze Shift + Command + Return**.

   ![Kliknij pozycję Zatrzymaj w programie Visual Studio](media/using-vsmac-tools-unity-image7.png)

> [!NOTE]
> Jeśli rozpoczęto debugowanie przy użyciu konfiguracji **Dołącz do unity i Play,** przycisk **Zatrzymaj** również zatrzyma jedność.

Aby dowiedzieć się więcej na temat debugowania w programie Visual Studio dla komputerów Mac, zobacz [Korzystanie z debugera](debugging.md).
