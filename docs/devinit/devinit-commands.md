---
title: Polecenia devinit
description: Szczegółowe informacje na temat sposobu instalowania składników przy użyciu poleceń devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d6c8f487fcb35fc210db57f0c8a49a2a86f909e9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672215"
---
# <a name="devinit-commands"></a>polecenia devinit

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

## <a name="init"></a>Init

```console
devinit init
```

Zainicjuj środowisko, uruchamiając narzędzia określone w [.devinit.js](devinit-json.md) pliku.

### <a name="options-for-init"></a>Opcje inicjowania

Opcjonalne opcje dla `devinit init` polecenia.

| Argument             | Wymagane | Opis                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -plik,--            | Nie       | Ścieżka do `.devinit.json` pliku.                                         |
| --błąd-akcja       | Nie       | Określa, jak obsługiwać błędy. Opcje: Stop, IGNORE, Continue (domyślnie).|
| -v,--verbose         | Nie       | Emituj pełne dane wyjściowe.                                                      |
| -n,--w trakcie działania suchego         | Nie       | Uruchomienie suche.                                                                  |

#### <a name="--file-argument"></a>--argument pliku

Określa ścieżkę do _devinit.js_ pliku. Jeśli nie określono parametru--File, szukamy pliku domyślnego w następujących lokalizacjach:

* {Current-Directory} \\.devinit.jsna
* {Current-Directory} \\devinit.jsna
* {Current-Directory} \\ . devinit \\.devinit.jsna
* {Current-Directory} \\ . devinit \\devinit.jsna
* {Current-Directory} \\ devinit \\.devinit.jsna
* {Current-Directory} \\ devinit \\devinit.jsna
* {Current-Directory} \\ . devcontainer \\.devinit.jsna
* {Current-Directory} \\ . devcontainer \\devinit.jsna

> [!NOTE]
> Jeśli zostanie znalezionych wiele plików domyślnych, devinit użyje pliku, który jest wyświetlany w pierwszej kolejności na powyższej liście.

#### <a name="--error-action-argument"></a>--Error-Action — argument

Zobacz [poniżej](#options-for-run).

#### <a name="--verbose-switch"></a>--pełny przełącznik

Zobacz [poniżej](#options-for-run).

#### <a name="--dry-run-switch"></a>--Przełącznik suchy

Zobacz [poniżej](#options-for-run).

## <a name="run"></a>Uruchom

```console
devinit run -t <toolname>
```

Uruchamia określone narzędzie, parametry są wymienione poniżej. Zapoznaj się z [dokumentacją](devinit-tool-list.md) każdego narzędzia pod kątem określonego użycia.

### <a name="options-for-run"></a>Opcje uruchamiania

Opcje `devinit run` polecenia.

| Argument                                      | Wymagane | Opis                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--narzędzie                                     | Tak      | Wymagane. Nazwa narzędzia.                                                             |
| -i,--dane wejściowe                                    | Nie       | Wartość wejściowa narzędzia. Na przykład nazwa pliku, pakietu lub nazwy.                     |
| --błąd-akcja                                | Nie       | Określa sposób obsługi błędów narzędzia: Stop, Ignoruj, Kontynuuj. Wartość domyślna to Zatrzymaj. |
| -v,--verbose                                  | Nie       | Emituj pełne dane wyjściowe.                                                                 |
| -n,--w trakcie działania suchego                                  | Nie       | Uruchomienie suche.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt; argN&gt;  | Nie       | Dodatkowe argumenty wiersza polecenia do narzędzia.                                       |

#### <a name="--error-action-argument"></a>--Error-Action — argument

Określa akcję, która ma zostać podjęta, jeśli narzędzie zwróci kod zakończenia różny od zera. Prawidłowe wartości to:

| Argument | Opis                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Kontynuuj przetwarzanie innych narzędzi po wyemitowaniu błędu do standardowego błędu. Kod zakończenia devinit.exe jest różny od zera (niepowodzenie). To zachowanie jest podobne do akcji zatrzymania błędu, ale przetwarzanie jest kontynuowane. `continue` jest domyślnym akcją błędu dla polecenia init.              |
| ignoruj   | Kontynuuj przetwarzanie innych narzędzi po wyemitowaniu ostrzeżenia do wyjścia standardowego. Kod zakończenia procesu DevInit powinien być zawsze równy zero (powodzenie). `ignore`Ustawienie ignoruje wszystkie błędy.                                                                                                      |
| zatrzymanie     | Emituje błąd do standardowego błędu i kończy przetwarzanie narzędzi. Kod zakończenia devinit.exe jest różny od zera (niepowodzenie). Jest to podobne do akcji Kontynuuj, ale podczas pierwszego napotkanego błędu przetwarzanie jest zatrzymywane. `stop` to domyślny błąd-akcja dla wszystkich poleceń z wyjątkiem init. |

#### <a name="--dry-run-switch"></a>--Przełącznik suchy

Polecenia narzędzia echo, które zostałyby uruchomione. Niektóre narzędzia mogą podejmować dalsze działania zgodnie z opisem dla tego narzędzia. 

#### <a name="--verbose-switch"></a>--pełny przełącznik

Emituj pełne dane wyjściowe do danych wyjściowych Standard. Jeśli narzędzie, które ma zostać wykonane, obsługuje opcję verbose, Propaguj pełny przełącznik do narzędzia.

#### <a name="--dry-run-switch"></a>--Przełącznik suchy

Polecenia narzędzia echo, które zostałyby uruchomione, ale nie wykonują żadnych narzędzi.

#### <a name="additional-command-line-arguments"></a>Dodatkowe argumenty wiersza polecenia

Użycie `<arg>` , które zawiera spację w jej wartości, musi zawierać dodatkową parę cudzysłowów ucieczkowych.

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

Aby zainstalować dotnet w określonym katalogu `C:\Program Files\dotnet` :

```console
devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Lista

```console
devinit list
```

Drukuje listę wszystkich dostępnych narzędzi.

## <a name="show"></a>Pokaż

```console
devinit show -t <toolname>
```

| Argument       | Wymagane | Opis                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--narzędzie      | Tak      | Wymagane. Nazwa narzędzia.                                                             |

Drukuje informacje pomocy dla danego narzędzia.

## <a name="version"></a>Wersja

```console
devinit version
```

Drukuje informacje o bieżącej wersji devinit.

## <a name="help"></a>Help

```console
devinit help
devinit help list
```

Drukuje tekst pomocy dla devinit lub dla określonego polecenia `devinit <command>` .
 
