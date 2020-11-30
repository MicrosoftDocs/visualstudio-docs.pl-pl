---
title: Pokrycie kodu — wyszukiwanie błędów
description: Dowiedz się, jak rozwiązywać błędne puste komunikaty wyników, gdy spodziewasz się, że program Visual Studio gromadzi dane dla zestawów natywnych i zarządzanych.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 7e960e0729e7d13b27d0c4fbda9b3f8eca0ac57c
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330124"
---
# <a name="troubleshoot-code-coverage"></a>Rozwiązywanie problemów z pokryciem kodu

Narzędzie analizy pokrycia kodu w programie Visual Studio zbiera dane dla zestawów natywnych i zarządzanych (pliki *. dll* lub *. exe* ). Jednak w niektórych przypadkach w oknie **wyników pokrycia kodu** jest wyświetlany komunikat o błędzie podobny do "wygenerowane puste wyniki:...". Istnieje kilka powodów, dla których można uzyskać puste wyniki. Ten artykuł pomaga rozwiązać te problemy.

## <a name="what-you-should-see"></a>Co powinno zostać wyświetlone

Jeśli wybierzesz polecenie **Analizuj pokrycie kodu** w menu **test** i jeśli kompilacja i testy zostaną wykonane pomyślnie, w oknie **pokrycie kodu** powinna zostać wyświetlona lista wyników. Aby wyświetlić szczegółowe informacje, należy rozwinąć elementy.

::: moniker range=">=vs-2019"
![Wyniki pokrycia kodu z kolorami](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Wyniki pokrycia kodu z kolorami](../test/media/codecoverage1.png)
::: moniker-end

Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Możliwe przyczyny braku wyników lub wyświetlania starych wyników

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Czy masz odpowiednią wersję programu Visual Studio?

Potrzebujesz Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nie zostały wykonane żadne testy

Analiza &mdash; Sprawdź okno dane wyjściowe. Na liście rozwijanej **Pokaż dane wyjściowe z** wybierz pozycję **testy**. Sprawdź, czy są zarejestrowane jakieś błędy lub ostrzeżenia.

Wyjaśnienie &mdash; analizy pokrycia kodu są wykonywane, gdy testy są uruchomione. Zawiera ona tylko te zestawy, które są ładowane do pamięci podczas wykonywania testów. Jeśli żaden z testów nie zostanie wykonany, nie ma niczego do zaraportowania.

&mdash;W Eksploratorze testów wybierz opcję **Uruchom wszystkie** , aby sprawdzić, czy testy zostały wykonane pomyślnie. Napraw wszystkie błędy przed użyciem **analizy pokrycia kodu**.

### <a name="youre-looking-at-a-previous-result"></a>Przeglądasz poprzedni wynik

Po zmodyfikowaniu i ponownym uruchomieniu testów można nadal wyświetlić poprzedni wynik pokrycia kodu, w tym kolorowanie kodu z tego starego przebiegu.

1. Uruchom **Analizowanie pokrycia kodu**.

2. Upewnij się, że wybrano najnowszy zestaw wyników w oknie **wyników pokrycia kodu** .

### <a name="pdb-symbol-files-are-unavailable"></a>Pliki .pdb (symbol) są niedostępne

Analiza &mdash; Otwórz folder docelowy kompilacji (zazwyczaj *bin\Debug*) i sprawdź, czy dla każdego zestawu znajduje się plik *. pdb* w tym samym katalogu, w którym znajduje się plik. *dll* lub *. exe* .

Wyjaśnienie &mdash; aparatu pokrycia kodu wymaga, aby każdy zestaw miał swój skojarzony plik *. pdb* dostępny podczas przebiegu testu. Jeśli nie istnieje plik *. pdb* dla określonego zestawu, zestaw nie jest analizowany.

Plik *. pdb* musi być wygenerowany z tej samej kompilacji co pliki *. dll* lub *. exe* .

Rozdzielczość upewnij &mdash; się, że ustawienia kompilacji generują plik *. pdb* . Jeśli pliki *. pdb* nie są aktualizowane po skompilowaniu projektu, Otwórz właściwości projektu, wybierz stronę **kompilacja** , wybierz pozycję **Zaawansowane** i sprawdź **informacje debugowania**.

W przypadku projektów języka C++ upewnij się, że wygenerowane pliki. pdb mają pełne informacje o debugowaniu. Otwórz właściwości projektu i sprawdź, czy **Linker**  >  **Debugging**  >  dla opcji **Wygeneruj informacje debugowania** dla debugowania konsolidatora jest ustawiona wartość **Generuj informacje o debugowaniu zoptymalizowane pod kątem udostępniania i publikowania (/Debug: Full)**.

Jeśli pliki *. pdb* i *. dll* lub *. exe* znajdują się w różnych miejscach, skopiuj plik *. pdb* do tego samego katalogu. Istnieje również możliwość skonfigurowania aparatu pokrycia kodu do wyszukiwania plików *. pdb* w innej lokalizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Używanie Instrumentacji lub zoptymalizowanych danych binarnych

Analiza &mdash; określa, czy plik binarny został poddany jakiejkolwiek formie zaawansowanej optymalizacji, takiej jak optymalizacja z przewodnikiem profilowego, lub jest Instrumentacją narzędzia profilowania, takiego jak *vsinstr.exe* lub *vsperfmon.exe*.

Wyjaśnienie &mdash; , jeśli zestaw został już Instrumentacją lub zoptymalizowany przez inne narzędzie profilowania, zestaw jest pomijany z analizy pokrycia kodu. Nie można przeprowadzić analizy pokrycia kodu na takich zestawach.

Wyłączono &mdash; optymalizację i wykorzystano nową kompilację.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod nie jest zarządzany (.NET) lub nie jest kodem natywnym (C++)

Analiza &mdash; sprawdza, czy uruchamiasz niektóre testy w kodzie zarządzanym lub C++.

Wyjaśnienie &mdash; analizy pokrycia kodu w programie Visual Studio są dostępne tylko w kodzie zarządzanym i natywnym (C++). Jeśli pracujesz z narzędziami innych firm, niektóre lub wszystkie kody mogą być wykonywane na innej platformie.

Rozwiązanie &mdash; nie jest dostępne.

### <a name="assembly-has-been-installed-by-ngen"></a>Zestaw został zainstalowany przez NGen

&mdash;Sprawdź, czy zestaw nie został załadowany z pamięci podręcznej obrazów natywnych.

Wyjaśnienie &mdash; ze względu na wydajność, zestawy obrazów natywnych nie są analizowane. Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Rozwiązanie &mdash; Użyj wersji MSIL zestawu. Nie Przetwarzaj go za pomocą narzędzia NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Niestandardowy plik .runsettings o złej składni

Analiza &mdash; Jeśli używasz pliku Custom *. runsettings* , może on zawierać błąd składniowy. Pokrycie kodu nie jest uruchamiane, a okno pokrycia kodu nie jest otwarte na końcu przebiegu testu lub zawiera stare wyniki.

Wyjaśnienie &mdash; można uruchomić testy jednostkowe z niestandardowym plikiem *. runsettings* , aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

&mdash;Możliwe jest rozwiązanie następujących typów błędów:

- **Błąd XML**

     Otwórz plik *. runsettings* w edytorze XML programu Visual Studio. Poszukaj oznak błędów.

- **Błąd wyrażenia regularnego**

  Każdy ciąg znaków w pliku jest wyrażeniem regularnym. Przejrzyj każdy z nich pod kątem błędów, a w szczególności Wyszukaj:

  - Niezgodne nawiasy (...) lub nawiasy klamrowe \\ (... \\ ). Jeśli chcesz dopasować nawiasy w ciągu wyszukiwania, musisz dodać przed nimi znak ucieczki. Na przykład aby dopasować do użycia funkcji: `.*MyFunction\(double\)`

  - Gwiazdka lub plus na początku wyrażenia. Aby dopasować dowolny ciąg znaków, użyj kropki, a po niej gwiazdki: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Niestandardowy plik .runsettings z niepoprawnymi wykluczeniami

Analiza &mdash; Jeśli używasz pliku Custom *. runsettings* , upewnij się, że zawiera on zestaw.

Wyjaśnienie &mdash; można uruchomić testy jednostkowe z niestandardowym plikiem *. runsettings* , aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozwiązanie &mdash; Usuń wszystkie `Include` węzły z pliku *. runsettings* , a następnie usuń wszystkie `Exclude` węzły. Jeśli to rozwiąże problem, umieść je z powrotem w etapach.

Upewnij się, że węzeł DataCollectors określa pokrycie kodu. Porównaj ją z przykładem w temacie [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Niektóre kody są zawsze wyświetlane jako niepokryte

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Kod inicjowania w natywnych bibliotekach DLL jest wykonywany przed instrumentacją

Analiza &mdash; statycznie połączonego kodu natywnego, część funkcji inicjującej **DllMain** i kod, który wywołuje, jest czasami wyświetlana jako nieobjęta, nawet jeśli kod został wykonany.

Wyjaśnienie &mdash; Narzędzia pokrycia kodu działa przez wstawianie instrumentacji do zestawu tuż przed uruchomieniem aplikacji. W każdym załadowanym wcześniej zestawie kod inicjujący w **DllMain** jest wykonywany zaraz po załadowaniu zestawu i przed uruchomieniem aplikacji. Ten kod wydaje się nie być objęty, co zwykle dotyczy zestawów ładowanych statycznie.

&mdash;Brak rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
