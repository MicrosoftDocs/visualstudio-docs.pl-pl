---
title: Rozwiązywanie problemów z pokryciem kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660377"
---
# <a name="troubleshooting-code-coverage"></a>Pokrycie kodu — wyszukiwanie błędów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie analizy pokrycia kodu w programie Visual Studio zbiera dane dotyczące zestawów natywnych i zarządzanych (pliki .dll i .exe). Jednak w niektórych przypadkach w oknie wyników pokrycia kodu jest wyświetlany komunikat o błędzie podobny do "wygenerowane puste wyniki:...". Istnieje kilka możliwych przyczyn tego problemu. Ten temat ma pomóc w rozwiązaniu tych problemów.

## <a name="what-you-should-see"></a>Co powinno zostać wyświetlone
 Jeśli wybierzesz polecenie **Analizuj pokrycie kodu** w menu test i jeśli kompilacja i testy zostaną wykonane pomyślnie, w oknie pokrycie kodu powinna zostać wyświetlona lista wyników. Aby wyświetlić szczegółowe informacje, należy rozwinąć elementy.

 ![Wyniki pokrycia kodu z kolorami](../test/media/codecoverage1.png "CodeCoverage1")

 Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Możliwe przyczyny braku wyników lub wyświetlania starych wyników

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Czy masz odpowiednią wersję programu Visual Studio?
 Potrzebujesz Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nie zostały wykonane żadne testy
 Analiza Sprawdź okno dane wyjściowe. Na liście rozwijanej **Pokaż dane wyjściowe z** wybierz pozycję **testy**. Sprawdź, czy są zarejestrowane jakieś błędy lub ostrzeżenia.

 Wyjaśnienie analizy pokrycia kodu są wykonywane, gdy testy są uruchomione. Zawiera ona tylko te zestawy, które są ładowane do pamięci podczas wykonywania testów. Jeśli nie są wykonywane żadne testy, narzędzie pokrycia kodu nie ma nic do zgłoszenia.

 W Eksploratorze testów wybierz opcję **Uruchom wszystkie** , aby sprawdzić, czy testy zostały wykonane pomyślnie. Napraw wszystkie błędy przed użyciem **analizy pokrycia kodu**.

### <a name="youre-looking-at-a-previous-result"></a>Patrzysz na poprzedni wynik
 Podczas modyfikowania i ponownego uruchamiania testów poprzedni wynik pokrycia kodu może być nadal widoczny, włącznie z kolorowaniem kodu z tego starego uruchamiania.

1. Uruchom analizę pokrycia kodu.

2. Upewnij się, czy wybrano zestaw najbardziej aktualnych wyników w oknie wyników Pokrycia kodu.

### <a name="pdb-symbol-files-are-unavailable"></a>Pliki .pdb (symbol) są niedostępne
 Analiza Otwórz folder docelowy kompilacji (zazwyczaj bin\Debug) i sprawdź, czy dla każdego zestawu istnieje plik. pdb w tym samym katalogu, w którym znajduje się plik. dll lub. exe.

 Wyjaśnienie aparatu pokrycia kodu wymaga, aby każdy zestaw miał swój skojarzony plik. pdb dostępny podczas przebiegu testu. Jeśli określony zestaw nie ma pliku .pdb, nie zostanie on przeanalizowany.

 Plik .pdb musi zostać wygenerowany z tej samej kompilacji co pliki .dll i .exe.

 Rozdzielczość upewnij się, że ustawienia kompilacji generują plik. pdb. Jeśli pliki. pdb nie są aktualizowane po skompilowaniu projektu, Otwórz właściwości projektu, wybierz stronę **kompilacja** , wybierz **Zaawansowane** i sprawdź **informacje debugowania**.

 Jeśli pliki .pdb i .dll lub .exe znajdują się w różnych miejscach, należy skopiować plik .pdb do tego samego katalogu. Można również skonfigurować silnik pokrycia kodu, aby wyszukiwał pliki .pdb w innej lokalizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Korzystanie ze zinstrumentowanego lub zoptymalizowanego pliku binarnego
 Analiza określa, czy plik binarny został poddany jakiejkolwiek formie zaawansowanej optymalizacji, takiej jak optymalizacja z przewodnikiem profilowego, lub jest Instrumentacją narzędzia profilowania, takiego jak vsinstr.exe lub vsperfmon.exe.

 Wyjaśnienie, jeśli zestaw został już Instrumentacją lub zoptymalizowany przez inne narzędzie profilowania, zestaw jest pomijany z analizy pokrycia kodu.

 Nie można wykonać analizy pokrycia kodu na takich zestawach.

 Wyłączono optymalizację i wykorzystano nową kompilację.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod nie jest zarządzany (.NET) lub nie jest kodem natywnym (C++)
 Analiza sprawdza, czy uruchamiasz niektóre testy na kodzie zarządzanym lub C++.

 Wyjaśnienie analizy pokrycia kodu w programie Visual Studio są dostępne tylko w kodzie zarządzanym i natywnym (C++). Jeżeli pracujesz na narzędziach innych firm, część kodu lub cały kod może być wykonywany na innej platformie.

 Rozwiązanie nie jest dostępne.

### <a name="assembly-has-been-installed-by-ngen"></a>Zestaw został zainstalowany przez NGen
 Sprawdź, czy zestaw nie został załadowany z pamięci podręcznej obrazów natywnych.

 Wyjaśnienie ze względu na wydajność, zestawy obrazów natywnych nie są analizowane. Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 Rozwiązanie Użyj wersji MSIL zestawu. Nie przetwarzaj go z NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Niestandardowy plik .runsettings o złej składni
 Analiza Jeśli używasz pliku Custom. runsettings, może on zawierać błąd składniowy.

 Wynikiem tego jest całkowity brak uruchomienia pokrycia kodu. Okno pokrycia kodu nie zostanie otwarte po zakończeniu przebiegu testowego lub pokaże stare wyniki.

 Wyjaśnienie można uruchomić testy jednostkowe z niestandardowym plikiem. runsettings, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

 Możliwe jest rozwiązanie następujących typów błędów:

- **Błąd XML**

     Otwórz plik .runsettings w edytorze XML programu Visual Studio. Poszukaj oznak błędów.

- **Błąd wyrażenia regularnego**

  Każdy ciąg znaków w pliku jest wyrażeniem regularnym. Przejrzyj każdy z nich w poszukiwaniu błędów, a w szczególności zwróć uwagę na:

  - Niezgodne nawiasy (...) lub nawiasy klamrowe \\ (... \\ ). Jeśli chcesz dopasować nawiasy w ciągu wyszukiwania, musisz dodać przed nimi znak ucieczki. Na przykład aby dopasować do użycia funkcji: `.*MyFunction\(double\)`

  - Gwiazdka lub plus na początku wyrażenia. Aby dopasować dowolny ciąg znaków, użyj kropki, a po niej gwiazdki: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Niestandardowy plik .runsettings z niepoprawnymi wykluczeniami
 Analiza Jeśli używasz pliku Custom. runsettings, upewnij się, że zawiera on zestaw.

 Wyjaśnienie można uruchomić testy jednostkowe z niestandardowym plikiem. runsettings, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

 Rozwiązanie Usuń wszystkie `Include` węzły z pliku. runsettings, a następnie usuń wszystkie `Exclude` węzły. Jeśli to rozwiąże problem, umieść je z powrotem w etapach.

 Upewnij się, że węzeł DataCollectors określa pokrycie kodu. Porównaj ją z przykładem w temacie [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Niektóre kody są zawsze wyświetlane jako niepokryte

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Kod inicjowania w natywnych bibliotekach DLL jest wykonywany przed instrumentacją
 Analiza statycznie połączonego kodu natywnego, część funkcji inicjującej **DllMain** i kod, który wywołuje, jest czasami wyświetlana jako nieobjęta, nawet jeśli kod został wykonany.

 Wyjaśnienie narzędzia pokrycia kodu działa przez wstawianie instrumentacji do zestawu tuż przed uruchomieniem aplikacji. W każdym zestawie załadowanym przed tym terminem kod inicjalizacji w **DllMain** jest wykonywany zaraz po załadowaniu zestawu i przed uruchomieniem aplikacji. Kod ten zostanie wyświetlony jako niepokryty.

 Zwykle dotyczy to statycznie załadowanych zestawów.

 Brak rozwiązania.

## <a name="see-also"></a>Zobacz też
 [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
