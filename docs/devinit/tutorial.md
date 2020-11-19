---
title: Samouczek
description: Samouczek dotyczący devinit.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7455a668bf78cc4c3badafa3fa1c3e9b4697a592
ms.sourcegitcommit: 3b9a8aec34c7e835069f4db5c133dd002028180c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94941378"
---
# <a name="tutorial"></a>Samouczek

W tym samouczku poznaszmy Konfigurowanie [repozytorium eShopOnWeb](https://github.com/andysterland/eShopOnWeb) za pomocą Devinit i Codespaces. W tym samouczku założono, że devinit jest już dostępny, zgodnie z opisem na [stronie pierwsze kroki](getting-started-with-devinit.md).

## <a name="step-1-determining-setup-steps"></a>Krok 1. Określanie kroków instalacji

Jak wspomniano na [stronie Wprowadzenie](getting-started-with-devinit.md), pierwszym krokiem jest zawsze określenie zależności i kroków konfiguracji, które ma projekt. Będzie się to różnić w zależności od konkretnego projektu, ale istnieje kilka pytań, które należy wziąć pod uwagę:

- Jakie środowiska uruchomieniowe lub zestawy SDK są zależne od projektu?
- Czy projekt wymaga pakietów (na przykład z czekolady)?
- Czy proces instalacji wymaga wykonania wszelkich akcji (na przykład uruchamiania skryptu)?
- Czy projekt ma niejawne zależności od wszystkich elementów, które są zainstalowane obok programu Visual Studio?
  - Jeśli tak jest, dobrym pomysłem jest również uwzględnienie ich w instalacji programu devinit. Dzięki temu można uniknąć sprzęgania się z instalacją programu Visual Studio.

Jednym z najlepszych metod określania tych informacji jest przeszukanie czynności konfiguracyjnych, które są obecnie dostępne dla repozytorium. W przypadku usługi eShopOnWeb istnieje kilka rzeczy, które należy obsłużyć:

- Instalowanie najnowszej wersji zestaw .NET Core SDK
- Instalowanie najnowszej wersji interfejsu wiersza polecenia programu .NET Entity Framework Core Tools
- Instalowanie SQL Server 2019 Express
- Używanie interfejsu wiersza polecenia platformy .NET Entity Framework do aktualizowania lokalnej bazy danych do najnowszej migracji

Następnie dowiesz się, jak wykonać wszystkie te działania w kontekście devinit.

## <a name="step-2-the-devinitjson"></a>Krok 2. .devinit.jsna

Najpierw chcemy skonstruować [.devinit.jsw pliku](devinit-json.md) i umieścić go w katalogu głównym repozytorium. Ten plik będzie zawierać serię kroków, które zostaną wykonane później w ramach `devinit init` polecenia. Aby określić, co należy uwzględnić w `.devinit.json` pliku, możemy skorzystać z naszej listy kroków instalacji i porównać do listy [narzędzi devinit](devinit-tool-list.md). Wykonajmy teraz kroki instalacji opisane powyżej.

| Krok                                                              | Czy devinit obsłużyć to dla nas?                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| Zainstaluj najnowszą zestaw .NET Core SDK                                      | **Tak**! Możemy użyć [ `require-dotnetcoresdk` Narzędzia](tool-require-dotnetcoresdk.md)                  |
| Instalowanie interfejsu wiersza polecenia narzędzi .NET Entity Framework Core Tools                      | **Tak**! Możemy użyć [ `dotnet-toolinstall` Narzędzia](tool-dotnet-toolinstall.md)                        |
| Zainstaluj SQL Server 2019 Express                                   | **Tak**! Możemy użyć [ `choco-install` Narzędzia](tool-choco-install.md)                                  |
| Aktualizowanie lokalnej bazy danych przy użyciu programu .NET Entity Framework                 | **Nie**, ale nadal osiągamy ten sposób, łącząc devinit z skryptem!                               |

Teraz, po czym już wiesz, Zacznijmy od warstwy Podstawowa `.devinit.json` . Dołączymy odwołanie do [ `.devinit.json` schematu](https://json.schemastore.org/devinit.schema-2.0)i pustą `run` sekcję:

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

Teraz Dodajmy kilka narzędzi.

Najpierw dodamy [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) . Z dokumentacji tego narzędzia można zobaczyć, że domyślne zachowanie polega na zainstalowaniu najnowszej wersji zestawu SDK. To dokładnie to, czego potrzebujemy, więc dodajmy go do naszego `.devinit.json` :

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

Następnie dodamy, [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) Aby zainstalować narzędzie na `dotnet-ef` całym świecie. Z dokumentacji zobaczymy, że możemy użyć `input` pola do określenia nazwy narzędzia i `additionalOptions` pola, aby określić zakres globalny:

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    }
  ]
}
```

W końcu dodamy [`choco-install`](tool-choco-install.md) do zainstalowania `sql-server-express` pakietu.

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    },
    {
      "comments": "Install SQL Server 2019 Express",
      "tool": "choco-install",
      "input": "sql-server-express"
    }
  ]
}
```

Teraz, `.devinit.json` gdy nasza praca została ukończona, możemy pracować nad skryptem instalacji, który będzie miał zadbać o uruchamianie devinit i aktualizowanie lokalnej bazy danych.

## <a name="step-3-the-setup-script"></a>Krok 3. skrypt instalacyjny

Aby obsługiwać uruchomione devinit i aktualizować lokalną bazę danych, utworzymy skrypt, który wykonuje potrzebne polecenia. Utwórzmy pusty skrypt programu PowerShell w naszym głównym repozytorium o nazwie `PostCloneSetup.ps1` . Najpierw dodamy wywołanie do `devinit init` :

```powershell
devinit init
```

Po wykonaniu tego `devinit init` działania zostaną uruchomione wszystkie narzędzia zdefiniowane w `run` sekcji naszego `.devinit.json` .

Na koniec chcemy wywołać `dotnet ef database update` aktualizację lokalnej bazy danych:

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

Po zakończeniu naszego skryptu instalacyjnego musimy dodać `.devcontainer.json` plik, który zostanie wykonany podczas instalacji codespace.

## <a name="step-4-the-devcontainerjson"></a>Krok 4. .devcontainer.jsna

Aby upewnić się, że nasz skrypt instalacyjny jest uruchamiany podczas tworzenia naszego codespace, użyjemy `.devcontainer.json` pliku. Podobnie jak w przypadku innych plików, należy umieścić je w katalogu głównym repozytorium.

W `.devcontainer.json` pliku należy tylko wywołać nasz skrypt Instalatora w ramach programu `postCreateCommand` . Zostanie to wykonane w ramach procesu tworzenia codespace:

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

I to wszystko.

## <a name="step-5-trying-it-out"></a>Krok 5. Próba wykonania tej czynności

Po wykonaniu naszych czynności instalacyjnych spróbujmy to zrobić w codespace na żywo przy użyciu [rzeczywistego repozytorium](https://github.com/andysterland/eShopOnWeb).

Najpierw utworzymy codespace przy użyciu programu Visual Studio:

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="Tworzenie codespace":::

Po rozpoczęciu tworzenia codespace możemy obejrzeć postęp procesu instalacji w programie `C:\.vsonline\.vsoshared\vmTerminal.dat` :

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="Obejrzyj postęp instalacji":::

Gdy wszystko będzie gotowe, uruchom aplikację za pomocą programu, `Web.csproj` Aby upewnić się, że wszystko działa prawidłowo:

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="Uruchamianie projektu":::

Po skompilowaniu i uruchomieniu aplikacji zobaczysz sklep w naszej przeglądarce internetowej:

:::image type="content" source="media/eshoponweb-live.png" alt-text="Wyświetlanie witryny":::

Dlatego nasz proces instalacji działał prawidłowo i teraz wszystko jest gotowe do opracowania w projekcie eShopOnWeb.
