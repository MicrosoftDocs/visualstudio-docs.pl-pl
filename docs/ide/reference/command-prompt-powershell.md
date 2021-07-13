---
title: Powłoki wiersza polecenia są & wiersza polecenia dla deweloperów
description: Zacznij od menu > wiersza polecenia. Visual Studio wiersz polecenia dla deweloperów, program PowerShell dla deweloperów i terminal umożliwiają łatwe korzystanie z narzędzi .NET i C++.
author: TerryGLee
ms.author: tglee
ms.date: 06/11/2021
ms.topic: reference
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fef783475304bb1faa1788bde591a22ed610d528
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649162"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio wiersz polecenia dla deweloperów i program PowerShell dla deweloperów

Visual Studio 2019 zawiera dwie powłoki wiersza polecenia dla deweloperów:

- **Visual Studio wiersz polecenia dla deweloperów** — standardowy wiersz polecenia z pewnymi zmiennymi środowiskowym ustawionymi w celu ułatwienia korzystania z narzędzi deweloperskiej wiersza polecenia. Dostępne od Visual Studio 2015 r.

- **Visual Studio PowerShell dla deweloperów** — bardziej zaawansowane niż wiersz polecenia. Na przykład można przekazać dane wyjściowe jednego polecenia (nazywanego *cmdlet* ) do innego cmdlet . Ta powłoka ma te same zmienne środowiskowe ustawione jako wiersz polecenia dla deweloperów. Dostępne od Visual Studio 2019 r.

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="wiersz polecenia dla deweloperów dla Visual Studio narzędzie clrver":::

Począwszy od Visual Studio 2019 r. w wersji 16.5, program Visual Studio zawiera **zintegrowany terminal,** który może hostuje jedną z tych powłok (wiersz polecenia dla deweloperów i program PowerShell dla deweloperów). Można również otworzyć wiele kart każdej powłoki. Terminal Visual Studio jest zbudowany na Terminal Windows [.](/windows/terminal/) Aby otworzyć terminal w Visual Studio, wybierz **pozycję Wyświetl**  >  **terminal.**

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Visual Studio z wieloma kartami":::

Otwarcie jednej z powłok dewelopera z usługi Visual Studio jako osobnej aplikacji lub w oknie Terminal powoduje otwarcie katalogu bieżącego rozwiązania (jeśli masz załadowane rozwiązanie). Takie zachowanie ułatwia uruchamianie poleceń dla rozwiązania lub jego projektów.

Obie powłoki mają określone zmienne środowiskowe, które umożliwiają łatwe korzystanie z narzędzi deweloperskiej wiersza polecenia. Po otwarciu jednej z tych powłok możesz wprowadzić polecenia dla różnych narzędzi bez konieczności wiedzieć, gdzie się znajdują. 

|Popularne polecenia|Opis|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Tworzenie projektu lub rozwiązania|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| Narzędzie [.NET Framework dla](/dotnet/framework/tools/index) CLR|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|Narzędzie [.NET Framework desembembera](/dotnet/framework/tools/index)|
|[`dotnet`](/dotnet/core/tools/dotnet)|Polecenie [interfejsu wiersza polecenia .NET](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|Polecenie [interfejsu wiersza polecenia .NET](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Narzędzie kompilacji języka C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Narzędzie kompilacji języka C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Narzędzie kompilacji C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Narzędzie kompilacji C/C++|


## <a name="start-in-visual-studio"></a>Rozpocznij w Visual Studio

Wykonaj następujące kroki, aby wiersz polecenia dla deweloperów program PowerShell dla deweloperów z poziomu Visual Studio:

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz pozycję **Narzędzia** Wiersz polecenia, wiersz polecenia dla deweloperów  >    >   program **PowerShell dla deweloperów.**

   ![Element menu wiersza polecenia w Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Rozpocznij z Windows menu

Innym sposobem uruchamiania powłok jest uruchomienie ich z menu Start. W zależności od wersji pakietu Visual Studio zainstalowanych dodatkowych zestawów SDK i obciążeń może być wyświetlanych wiele wiersza polecenia. 

### <a name="windows-10"></a>Windows 10

1. Wybierz **pozycję Windows** logo na ![ klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) i przewiń do litery **V**.

1. Rozwiń **folder Visual Studio 2019.**

1. Wybierz **wiersz polecenia dla deweloperów vs 2019** lub program PowerShell dla deweloperów **dla programu VS 2019.**

   Alternatywnie możesz rozpocząć wpisywanie nazwy powłoki w polu wyszukiwania na pasku zadań i wybrać odpowiedni wynik, ponieważ na liście wyników zaczną być wyświetlane dopasowania wyszukiwania.

   ![Animowany plik GIF przedstawiający zachowanie wyszukiwania Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Przejdź do ekranu **startowego,** naciskając klawisz Windows logo Windows ![ klawisz logo na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na klawiaturze.

1. Na **ekranie startowym** naciśnij klawisz **Ctrl,** +  aby otworzyć **listę Aplikacje,** a następnie naciśnij klawisz **V**. Zostanie wyświetlona lista, która zawiera wszystkie zainstalowane Visual Studio wiersza polecenia.

1. Wybierz **wiersz polecenia dla deweloperów vs 2019** lub program PowerShell dla deweloperów **dla programu VS 2019.**

### <a name="windows-7"></a>Windows 7

1. Wybierz **pozycję Start,** a następnie **rozwiń pozycję Wszystkie programy.**

1. Wybierz **Visual Studio 2019** Visual Studio Tools wiersz polecenia dla deweloperów vs 2019 lub program PowerShell dla deweloperów w  >    >   **programie VS 2019.**

   ![Windows 7 menu Start wyróżniony wiersz polecenia](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Jeśli masz zainstalowane inne zestawy [SDK,](https://developer.microsoft.com/windows/downloads/windows-10-sdk) takie jak Windows 10 SDK lub poprzednie [wersje,](https://developer.microsoft.com/windows/downloads/sdk-archive)mogą pojawić się dodatkowe monity o polecenia. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="start-from-file-browser"></a>Rozpoczynanie pracy z przeglądarką plików 

Zazwyczaj skróty dla zainstalowanych powłok są umieszczane w folderze **Menu Start** dla programu Visual Studio, na przykład w folderze *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*. Jeśli jednak wyszukiwanie w wierszu polecenia nie da oczekiwanych wyników, możesz spróbować ręcznie zlokalizować pliki na maszynie.

### <a name="developer-command-prompt"></a>Wiersz polecenia dla deweloperów

Wyszukaj nazwę pliku wiersza polecenia, *czyliVsDevCmd.bat*, lub przejdź do folderu Tools dla programu Visual Studio, takiego jak *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (ścieżka zmienia się w zależności od wersji, edycji i lokalizacji instalacji programu Visual Studio).

Po zlokalizowaniu pliku wiersza polecenia otwórz go, wprowadzając następujące polecenie w regularnym oknie wiersza polecenia:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Lub wprowadź następujące polecenie w oknie dialogowym Windows **Uruchom:**

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Należy edytować ścieżkę, aby dopasować do Visual Studio instalacji.

### <a name="developer-powershell"></a>Program PowerShell dla deweloperów

Wyszukaj plik skryptu programu PowerShell o nazwie *Launch-VsDevShell.ps1* lub przejdź do folderu Tools dla programu Visual Studio, takiego jak *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools.* (Ścieżka zmienia się w zależności Visual Studio wersji, wersji i lokalizacji instalacji. Po zlokalizowaniu pliku programu PowerShell uruchom go, wprowadzając następujące polecenie w wierszu Windows PowerShell lub PowerShell 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Domyślnie uruchamiany program PowerShell dla deweloperów jest konfigurowany dla instalacji programu Visual Studio, w której znajduje się *Launch-VsDevShell.ps1* instalacji.

> [!TIP]
> Aby [można było uruchomić](/powershell/module/microsoft.powershell.core/about/about_execution_policies) program , należy ustawić zasady cmdlet wykonywania.

## <a name="see-also"></a>Zobacz też

- [Terminal Windows](/windows/terminal/)
- [Narzędzia programu .NET Framework](/dotnet/framework/tools/index)
- [Używanie zestawu narzędzi języka Microsoft C++ z wiersza polecenia](/cpp/build/building-on-the-command-line)
- [Visual Studio Code użytkowników](https://code.visualstudio.com/docs/cpp/config-msvc#:~:text=To%20open%20the%20Developer%20Command,item%20to%20open%20the%20prompt.)
