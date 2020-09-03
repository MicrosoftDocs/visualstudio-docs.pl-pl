---
title: Debugowanie szablonu tekstowego T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1570061feb5da034e2e8fab7168658577f6f990d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589685"
---
# <a name="debugging-a-t4-text-template"></a>Debugowanie szablonu tekstowego T4
Możesz ustawić punkty przerwania w szablonach tekstowych. Aby debugować szablon tekstu czasu projektowania, Zapisz plik szablonu tekstu, a następnie wybierz **Debuguj szablon T4** w menu skrótów pliku w Eksplorator rozwiązań. Aby debugować szablon tekstu czasu wykonywania, po prostu Debuguj aplikację, do której należy.

 Aby debugować szablon tekstowy, należy zapoznać się z krokami procesu transformacji szablonu. W każdym kroku mogą wystąpić różne rodzaje błędów. Kroki są następujące.

|Krok|Szablon czasu projektowania: gdy wystąpi|Szablon czasu wykonywania: gdy wystąpi|
|-|-|-|
|Kod jest generowany na podstawie szablonu tekstu.<br /><br /> Błędy w dyrektywach lub niezgodne lub nieuporządkowane `<#...#>` Tagi.|Podczas zapisywania szablonu lub wywołaj transformację tekstu.|Podczas zapisywania szablonu lub wywołaj transformację tekstu.|
|Wygenerowany kod został skompilowany.<br /><br /> Błędy kompilacji w kodzie szablonu.|Natychmiast po poprzednim kroku.|Wraz z kodem aplikacji.|
|Kod jest uruchamiany.<br /><br /> Błędy w czasie wykonywania w kodzie szablonu.|Natychmiast po poprzednim kroku.|Gdy aplikacja jest uruchomiona i wywołuje kod szablonu.|

 W większości przypadków numery wierszy w kodzie szablonu są podane w raporcie o błędach. Gdy raport o błędach odwołuje się do tymczasowej nazwy pliku, typową przyczyną jest niedopasowany nawias w kodzie szablonu tekstu.

 Można ustawić punkty przerwania w szablonach tekstowych i debugować w zwykły sposób.

## <a name="common-errors-and-fixes"></a>Typowe błędy i poprawki
 W poniższej tabeli wymieniono najbardziej typowe błędy i ich poprawki.

|Komunikat o błędzie|Opis|Rozwiązanie|
|-|-|-|
|Nie można załadować klasy podstawowej " {0} ", z której dziedziczy Klasa transformacji.|Występuje, jeśli nie można znaleźć klasy bazowej określonej w `inherits` parametrze w dyrektywie szablonu. Komunikat zawiera numer wiersza dyrektywy szablonu.|Upewnij się, że określona Klasa istnieje i że zestaw, w którym istnieje, jest określony w dyrektywie zestawu.|
|Nie można rozpoznać tekstu dyrektywy include dla pliku:{0}|Występuje, gdy nie można znaleźć dołączonego szablonu. Komunikat zawiera nazwę żądanego pliku dołączanego.|Upewnij się, że ścieżka pliku jest względna w stosunku do oryginalnej ścieżki szablonu lub że plik znajduje się w lokalizacji, która jest zarejestrowana w hoście lub że istnieje pełna ścieżka do pliku.|
|Podczas inicjowania obiektu transformacji zostały wygenerowane błędy. Transformacja nie zostanie uruchomiona.|Występuje, gdy element "Initialize ()" klasy transformacji zakończył się niepowodzeniem lub zwrócił wartość false.|Kod w funkcji Initialize () pochodzi z podstawowej klasy transformacji określonej w \<#@template#> dyrektywie i z procesorów dyrektywy. Błąd, który spowodował zainicjowanie niepowodzenia, prawdopodobnie znajduje się na liście błędów. Zbadaj przyczynę niepowodzenia. Aby debugować szablon, można sprawdzić rzeczywisty wygenerowany kod dla inicjowania ().|
|Zestaw {0} uprawnień FullTrust dla zestawu "" dla procesora dyrektywy " {1} " nie został przydzielony. Tylko zaufane zestawy mogą udostępniać procesory dyrektywy. Ten procesor dyrektywy nie zostanie załadowany.|Występuje, gdy system nie przyznaje uprawnień FullTrust do zestawu zawierającego procesor dyrektywy. Komunikat zawiera nazwę zestawu i nazwę procesora dyrektywy.|Upewnij się, że tylko zaufane zestawy są używane tylko na komputerze lokalnym.|
|Ścieżka " {0} " musi być lokalna dla tego komputera lub części zaufanej strefy.|Występuje, gdy dyrektywa lub dyrektywa Assembly odwołuje się do pliku, który nie znajduje się na komputerze lokalnym lub w zaufanej strefie sieci.|Upewnij się, że katalog, w którym znajduje się dyrektywa lub dyrektywy zestawu, znajduje się w zaufanej strefie. W programie Internet Explorer możesz dodać Katalog sieciowy do zaufanej strefy.|
|Wiele błędów składni, takich jak "nieprawidłowy token" Catch "" lub "Przestrzeń nazw nie może bezpośrednio zawierać składowych"|Zbyt wiele zamykających nawiasów klamrowych w kodzie szablonu. Kompilator jest mylący przy użyciu standardowego kodu generacji.|Sprawdź liczbę zamykających nawiasów klamrowych i nawiasów wewnątrz ograniczników kodu.|
|Pętle lub warunkowe nie są kompilowane lub wykonywane poprawnie. Na przykład: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Ten kod zawsze wyprowadza wartość i. Tylko "Number is:" jest warunkowo.|W języku C#, zawsze używaj nawiasów klamrowych do otaczania bloków tekstowych, które są osadzone w instrukcjach sterowania.|Dodaj nawiasy klamrowe: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|"Wyrażenie jest zbyt złożone" podczas przetwarzania szablonu czasu projektowania lub kompilowania szablonu środowiska uruchomieniowego (wstępnie przetworzonego).<br /><br /> Program Visual Studio przestaje działać podczas próby sprawdzenia kodu wygenerowanego przez szablon środowiska uruchomieniowego.|Blok tekstowy jest zbyt długi. T4 konwertuje bloki tekstu na wyrażenie łączenia ciągów, z jednym literałem ciągu dla każdego wiersza szablonu. Bardzo długie bloki tekstu mogą przekroczyć limity rozmiaru kompilatora.|Podziel długi blok tekstu na blok wyrażenia, taki jak:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Opisy i poprawki ostrzeżeń
 W poniższej tabeli wymieniono najbardziej typowe ostrzeżenia wraz z poprawkami, jeśli są dostępne.

|Komunikat ostrzegawczy|Opis|Rozwiązanie|
|-|-|-|
|Załadowanie pliku dołączanego " {0} " zwróciło wartość null lub pusty ciąg.|Występuje, gdy dołączony plik szablonu tekstowego jest pusty. Komunikat zawiera nazwę pliku dołączonego.|Usuń dyrektywę include lub upewnij się, że plik ma pewną zawartość.|
|Kompilowanie transformacji:|Dołącza ten ciąg do wszystkich błędów lub ostrzeżeń pochodzących z kompilatora, gdy kompiluje przekształcenie. Ten ciąg oznacza, że kompilator zgłosił błąd lub ostrzeżenie.|Jeśli wystąpi problem z znalezieniem biblioteki DLL, może być konieczne podanie pełnej ścieżki lub w pełni kwalifikowanej silnej nazwy, jeśli biblioteka DLL znajduje się w pamięci GAC.|
|Parametr " {0} " już istnieje w dyrektywie. Zduplikowany parametr zostanie zignorowany.|Występuje, gdy parametr jest określony więcej niż raz w dyrektywie. Komunikat zawiera nazwę parametru i numer wiersza dyrektywy.|Usuń specyfikację powielonego parametru.|
|Wystąpił błąd podczas ładowania pliku dołączonego " {0} ". Dyrektywa include zostanie zignorowana.|Występuje, gdy nie można znaleźć pliku określonego w `include` dyrektywie. Komunikat zawiera nazwę pliku i numer wiersza dyrektywy.|Upewnij się, że plik dołączania istnieje w tym samym katalogu co plik oryginalnego szablonu tekstu lub w jednym z katalogów dołączania zarejestrowanych z hostem.|
|Określono nieprawidłową klasę bazową dla klasy transformacji. Klasa bazowa musi pochodzić od Microsoft. VisualStudio. TextTemplating. TextTransformation.|Występuje, gdy `inherits` parametr w dyrektywie Template określa klasę, która nie dziedziczy z `TextTransformation` . Komunikat zawiera numer wiersza dyrektywy szablonu.|Określ klasę, która pochodzi od `TextTransformation` .|
|Określono nieprawidłową kulturę w dyrektywie "template". Kultura musi być w formacie XX-XX. Zostanie użyta Niezmienna kultura.|Występuje, gdy parametr Culture w dyrektywie Template zostanie określony nieprawidłowo. Komunikat zawiera numer wiersza dyrektywy szablonu.|Zmień parametr Culture na prawidłową kulturę w formacie "XX-XX".|
|Określono nieprawidłową wartość debugowania " {0} " w dyrektywie Template. Wartość debugowania musi być równa "true" lub "false". Zostanie użyta wartość domyślna "false".|Występuje, gdy `debug` parametr w dyrektywie Template zostanie określony nieprawidłowo. Komunikat zawiera numer wiersza dyrektywy szablonu.|Ustaw parametr Debug na wartość "true" lub "false".|
|Określono nieprawidłową wartość HostSpecific " {0} " w dyrektywie Template. Wartość HostSpecific musi być równa "true" lub "false". Zostanie użyta wartość domyślna "false".|Występuje, gdy parametr specyficzny dla hosta w `template` dyrektywie zostanie określony nieprawidłowo. Komunikat zawiera numer wiersza dyrektywy szablonu.|Ustaw parametr specyficzny dla hosta na wartość "true" lub "false".|
|Określono nieprawidłowy język " {0} " w dyrektywie "template". Język musi mieć wartość "C#" lub "VB". Zostanie użyta wartość domyślna "C#".|Występuje, gdy w dyrektywie zostanie określony nieobsługiwany język `template` . Dozwolone są tylko języki "C#" lub "VB" (bez uwzględniania wielkości liter). Komunikat zawiera numer wiersza dyrektywy szablonu.|Ustaw `language` parametr w dyrektywie Template na "C#" lub "VB".|
|W szablonie znaleziono wiele dyrektyw wyjściowych. Wszystkie oprócz pierwszej z nich zostaną zignorowane.|Występuje, gdy `output` w pliku szablonu określono wiele dyrektyw. Komunikat zawiera numer wiersza dyrektywy dotyczącej zduplikowanych danych wyjściowych.|Usuń zduplikowane `output` dyrektywy.|
|W szablonie znaleziono wiele dyrektyw Template. Wszystkie oprócz pierwszej z nich zostaną zignorowane. W ramach jednej dyrektywy szablonu należy określić wiele parametrów dyrektywy Template.|Występuje w przypadku określenia wielu `template` dyrektyw w pliku szablonu tekstu (w tym dołączonych plików). Komunikat zawiera numer wiersza dyrektywy duplikatu szablonu.|Agreguj różne `template` dyrektywy do jednej `template` dyrektywy.|
|Nie określono procesora dla dyrektywy o nazwie " {0} ". Dyrektywa zostanie zignorowana.|Występuje, gdy określisz `custom` dyrektywę, ale nie podasz `processor` atrybutu. Komunikat zawiera nazwę dyrektywy i numer wiersza.|Podaj `processor` atrybut o nazwie `directive` procesora dla dyrektywy.|
|Nie można odnaleźć procesora o nazwie " {0} " dla dyrektywy o nazwie " {1} ". Dyrektywa zostanie zignorowana.|Występuje, gdy system nie może znaleźć `directive` procesora określonego w `custom` dyrektywie. Komunikat zawiera nazwę dyrektywy, nazwę procesora i numer wiersza dyrektywy.|Ustaw `processor` atrybut w dyrektywie na nazwę procesora dyrektywy.|
|Nie znaleziono wymaganego parametru " {0} " dla dyrektywy " {1} ". Dyrektywa zostanie zignorowana.|Występuje, gdy system nie dostarcza wymaganego parametru dyrektywy. Komunikat zawiera nazwę brakującego parametru, nazwę dyrektywy i numer wiersza.|Podaj brakujący parametr.|
|Procesor o nazwie " {0} " nie obsługuje dyrektywy o nazwie " {1} ". Dyrektywa zostanie zignorowana.|Występuje, gdy procesor dyrektywy nie obsługuje dyrektywy. Komunikat zawiera nazwę i numer wiersza dyrektywy, która jest poprawna, wraz z nazwą procesora dyrektywy.|Popraw nazwę dyrektywy.|
|Dyrektywa include dla pliku " {0} " powoduje nieskończoną pętlę.|Wyświetlany, jeśli określono cykliczne dyrektywy include (na przykład plik A zawiera plik B, który zawiera plik A).|Nie określaj dyrektyw dołączania cyklicznego.|
|Uruchomiono transformację:|Dołącza ten ciąg do wszystkich błędów lub ostrzeżeń, które są generowane podczas wykonywania transformacji.|Nie dotyczy.|
|W bloku znaleziono nieoczekiwany tag początkowy lub końcowy. Upewnij się, że nie został wpisany nieprawidłowy tag początkowy lub końcowy oraz że nie masz żadnych zagnieżdżonych bloków w szablonie.|Wyświetlane, gdy masz nieoczekiwany \<# or #> . Oznacza to, że jeśli masz \<# after another open tag that has not been closed, or you have a #> niezamknięty tag otwarty przed nim. Komunikat zawiera numer wiersza niezgodnego tagu.|Usuń niezgodny tag początkowy lub końcowy lub użyj znaku ucieczki.|
|Dyrektywa została określona w niewłaściwym formacie. Dyrektywa zostanie zignorowana. Określ dyrektywę w formacie `<#@ name [parametername="parametervalue"]*  #>`|Wyświetlane przez parser, jeśli dyrektywa nie jest określona w poprawnym formacie. Komunikat zawiera numer wiersza dla nieprawidłowej dyrektywy.|Upewnij się, że wszystkie dyrektywy mają postać `<#@ name [parametername="parametervalue"]*  #>` . Aby uzyskać więcej informacji, zobacz [dyrektywy dotyczące szablonów tekstowych T4](../modeling/t4-text-template-directives.md).|
|Nie można załadować zestawu " {0} " dla zarejestrowanego procesora dyrektywy " {1} "<br /><br /> {2}|Występuje, gdy procesor dyrektywy nie może zostać załadowany przez hosta. Komunikat identyfikuje zestaw dostarczony dla procesora dyrektywy i nazwę procesora dyrektywy.|Upewnij się, że procesor dyrektywy jest poprawnie zarejestrowany i że zestaw istnieje.|
|Nie można znaleźć typu " {0} " w zestawie " {1} " dla zarejestrowanego procesora dyrektywy " {2} "<br /><br /> {3}|Występuje, gdy nie można załadować typu procesora dyrektywy z jego zestawu. Komunikat zawiera nazwę typu, zestawu i procesora dyrektywy.|Vshost odnajduje informacje o procesorze dyrektywy (nazwa, zestaw i typ) w rejestrze. Upewnij się, że procesor dyrektywy jest poprawnie zarejestrowany i że typ istnieje w zestawie.|
|Wystąpił problem podczas ładowania zestawu " {0} "|Występuje, gdy wystąpił problem podczas ładowania zestawu. Komunikat zawiera nazwę zestawu.|Można określić zestawy do załadowania w \<@#assembly#> dyrektywach i przez procesory dyrektywy. Komunikat o błędzie, który następuje po tym ciągu powinien dostarczyć więcej danych na temat przyczyny niepowodzenia ładowania zestawu.|
|Wystąpił problem podczas tworzenia i inicjowania procesora dla dyrektywy o nazwie " {1} ". Typ procesora to {0} . Dyrektywa zostanie zignorowana.|Występuje, gdy system nie może utworzyć lub zainicjować procesora dyrektywy. Komunikat zawiera nazwę i numer wiersza dyrektywy oraz typ procesora.|Upewnij się, że używasz prawidłowego procesora dyrektywy i że procesor dyrektywy ma publiczny Konstruktor domyślny. W przeciwnym razie użyj opcji debugowania, aby dowiedzieć się, dlaczego metoda Initialize () procesora dyrektywy kończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz temat [Rozwiązywanie problemów z szablonami tekstu](../modeling/debugging-a-t4-text-template.md).|
|Zgłoszono wyjątek podczas przetwarzania dyrektywy o nazwie " {0} ".|Występuje, gdy procesor dyrektywy zgłasza wyjątek podczas przetwarzania dyrektywy.|Upewnij się, że parametry procesora dyrektywy są poprawne.|
|Host zgłosił wyjątek podczas próby rozpoznania odwołania do zestawu " {0} ".|Występuje, gdy host zgłasza wyjątek podczas próby rozpoznania odwołania do zestawu. Komunikat zawiera ciąg odwołania do zestawu.|Odwołania do zestawów pochodzą z \<@#assembly#> dyrektyw i z procesorów dyrektywy. Upewnij się, że parametr "name" podany w parametrze Assembly jest poprawny.|
|Próba określenia nieobsługiwanej {1} wartości " {0} " dla dyrektywy {2}|Występuje przez RequiresProvidesDirectiveProcessor (wszystkie z naszych wygenerowanych procesorów dyrektywy dziedziczy z niej), gdy podasz nieobsługiwane lub zawiera argument.|Upewnij się, że nazwy w parach Name = "value" podane w wymaganiach i udostępnia parametry są poprawne.|
