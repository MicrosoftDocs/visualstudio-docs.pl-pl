---
title: Powłoki wiersza polecenia dla deweloperów
description: Dowiedz się, jak znaleźć i korzystać z programu Visual Studio wiersz polecenia dla deweloperów, Visual Studio Developer PowerShell i terminala programu Visual Studio, dzięki czemu można łatwiej korzystać z narzędzi .NET i C++.
ms.date: 03/04/2021
ms.custom: contperf-fy21q3
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fb2c99037577528b77ab5c1b0c74bf7af9e73d1b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672328"
---
# <a name="developer-command-prompt-and-developer-powershell"></a>wiersz polecenia dla deweloperów i deweloper programu PowerShell

Program Visual Studio 2019 zawiera dwie powłoki wiersza polecenia dla deweloperów:

- **Visual Studio wiersz polecenia dla deweloperów** — standardowy wiersz polecenia z pewnymi zmiennymi środowiskowymi ustawionymi przy użyciu narzędzi deweloperskich wiersza polecenia. Dostępne od programu Visual Studio 2015.
- **Visual Studio Developer PowerShell** — bardziej wydajny niż wiersz polecenia. Na przykład można przekazać dane wyjściowe jednego polecenia (znanego jako a *cmdlet* ) do innego cmdlet . Ta powłoka ma te same zmienne środowiskowe ustawione jako wiersz polecenia dla deweloperów. Dostępne od programu Visual Studio 2019.

Obie powłoki mają określone zmienne środowiskowe, które umożliwiają łatwiejsze korzystanie z narzędzi deweloperskich wiersza polecenia. Po otwarciu jednej z tych powłok można wprowadzić polecenia dla różnych narzędzi, bez konieczności wiedzieć, gdzie się znajdują. Polecenia, które można uruchomić, obejmują:

- [`MSBuild`](../../msbuild/msbuild-command-line-reference.md), aby skompilować projekt lub rozwiązanie.
- [.NET Framework narzędzia](/dotnet/framework/tools/index), takie jak [`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool) i [`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler) .
- Narzędzia kompilacji C/C++, takie jak [`CL`](/cpp/build/reference/compiler-command-line-syntax) i [`NMAKE`](/cpp/build/reference/running-nmake) .
- Dodatkowe narzędzia do kompilacji C/C++, takie jak [`LIB`](/cpp/build/reference/lib-reference) i [`DUMPBIN`](/cpp/build/reference/dumpbin-reference) .
- [Poleceń interfejsu wiersza polecenia platformy .NET](/dotnet/core/tools/index), takich jak [`dotnet`](/dotnet/core/tools/dotnet) i [`dotnet run`](/dotnet/core/tools/dotnet-run) . (Te polecenia są również dostępne w zwykłym wierszu polecenia).

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="wiersz polecenia dla deweloperów dla programu Visual Studio z pokazywaniem narzędzia Clrver":::

Począwszy od programu Visual Studio 2019 w wersji 16,5, program Visual Studio zawiera zintegrowany **Terminal** , który może hostować jedną z tych powłok (wiersz polecenia dla deweloperów i deweloper programu PowerShell). Można również otworzyć wiele kart każdej powłoki. Terminal programu Visual Studio jest oparty na [terminalu systemu Windows](/windows/terminal/). Aby otworzyć Terminal w programie Visual Studio, wybierz pozycję **Wyświetl**  >  **Terminal**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Terminal programu Visual Studio pokazujący wiele kart":::

Po otwarciu jednej z powłok dla deweloperów w programie Visual Studio jako osobna aplikacja lub w oknie terminalu zostanie otwarta w katalogu bieżącego rozwiązania (Jeśli masz załadowane rozwiązanie). Takie zachowanie ułatwia uruchamianie poleceń względem rozwiązania lub jego projektów.

## <a name="start-the-shell-from-inside-visual-studio"></a>Uruchom powłokę z programu Visual Studio

Wykonaj następujące kroki, aby otworzyć wiersz polecenia dla deweloperów lub deweloper programu PowerShell z poziomu programu Visual Studio:

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz **Narzędzia**  >  **wiersz polecenia**  >  **wiersz polecenia dla deweloperów** lub **deweloper programu PowerShell**.

   ![Element menu wiersza polecenia w programie Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="use-the-windows-start-menu"></a>Korzystanie z menu Start systemu Windows

W zależności od wersji programu Visual Studio i wszelkich dodatkowych zestawów SDK i obciążeń, które zostały zainstalowane, może być wiele wierszy poleceń. Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na maszynie](#manually-locate-the-file) lub [uruchomić powłokę z poziomu programu Visual Studio](#start-the-shell-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Wybierz pozycję **Uruchom** ![ klucz logo systemu Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) i przewiń do litery **V**.

1. Rozwiń folder **programu Visual Studio 2019** .

1. Wybierz **wiersz polecenia dla deweloperów dla programu vs 2019** lub **dewelopera POWERSHELL dla programu vs 2019**.

   Alternatywnie możesz zacząć wpisywać nazwę powłoki w polu wyszukiwania na pasku zadań, a następnie wybrać wynik, który zostanie wyświetlony na liście wyników wyszukiwania.

   ![Animowany plik GIF pokazujący zachowanie wyszukiwania w systemie Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![ na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na przykład na klawiaturze.

1. Na ekranie **startowym** naciśnij klawisz **Ctrl**, +  aby otworzyć listę **aplikacje** , a następnie naciśnij klawisz **V**. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.

1. Wybierz **wiersz polecenia dla deweloperów dla programu vs 2019** lub **dewelopera POWERSHELL dla programu vs 2019**.

### <a name="windows-7"></a>Windows 7

1. Wybierz przycisk **Start** , a następnie rozwiń pozycję **Wszystkie programy**.

1. Wybierz pozycję **Visual Studio 2019**  >  **Visual Studio Tools**  >  **wiersz polecenia dla deweloperów dla programu vs 2019** lub **Developer PowerShell dla programu vs 2019**.

   ![Menu Start systemu Windows 7 z wyróżnionym wierszem polecenia](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Jeśli zainstalowano inne zestawy SDK, takie jak [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), mogą pojawić się dodatkowe polecenia. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="manually-locate-the-file"></a>Ręczne lokalizowanie pliku

Zazwyczaj skróty zainstalowanych powłok są umieszczane w folderze **menu Start** dla programu Visual Studio, na przykład w programie *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*. Jeśli jednak wyszukiwanie w wierszu polecenia nie daje oczekiwanych wyników, możesz spróbować ręcznie zlokalizować pliki na komputerze.

### <a name="developer-command-prompt"></a>Wiersz polecenia dla deweloperów

Wyszukaj nazwę pliku wiersza polecenia, który jest *VsDevCmd.bat* lub przejdź do folderu Tools dla programu Visual Studio, takiego jak *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (zmiany ścieżki według wersji programu Visual Studio, wersji i lokalizacji instalacji).

Po zlokalizowaniu pliku wiersza polecenia Otwórz go, wprowadzając następujące polecenie w zwykłym oknie wiersza polecenia:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Lub wprowadź następujące polecenie w oknie dialogowym **Uruchamianie** systemu Windows:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Musisz edytować ścieżkę, aby dopasować ją do instalacji programu Visual Studio.

### <a name="developer-powershell"></a>Program PowerShell dla deweloperów

Wyszukaj plik skryptu programu PowerShell o nazwie *Launch-VsDevShell.ps1* lub przejdź do folderu Tools dla programu Visual Studio, takiego jak *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools*. (Ścieżka zmienia się w zależności od wersji programu Visual Studio, wersji i lokalizacji instalacji). Po umieszczeniu pliku programu PowerShell uruchom go, wprowadzając następujące polecenie w programie Windows PowerShell lub w wierszu polecenia programu PowerShell 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Domyślnie Deweloper programu PowerShell, który zostanie uruchomiony, jest skonfigurowany dla instalacji programu Visual Studio, której ścieżka instalacji znajduje się w pliku *Launch-VsDevShell.ps1* .

> [!TIP]
> Aby można było uruchomić, należy ustawić [zasady wykonywania](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlet .

## <a name="see-also"></a>Zobacz też

- [Program PowerShell dla deweloperów](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Powiedz Witaj na nowym terminalu programu Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Terminal systemu Windows](/windows/terminal/)
- [Narzędzia programu .NET Framework](/dotnet/framework/tools/index)
- [Zarządzanie narzędziami zewnętrznymi](../managing-external-tools.md)
- [Używanie zestawu narzędzi platformy Microsoft C++ w wierszu polecenia](/cpp/build/building-on-the-command-line)
