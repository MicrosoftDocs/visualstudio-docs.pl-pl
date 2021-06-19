---
title: Debugowanie szablonu tekstowego T4
description: Aby debugować szablon tekstowy czasu projektowania, zapisz plik szablonu tekstowego, a następnie wybierz pozycję Debuguj szablon T4 w menu skrótów pliku w Eksplorator rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c9e4454071002e3bce8478bc825ecfddc17620f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385776"
---
# <a name="debugging-a-t4-text-template"></a>Debugowanie szablonu tekstowego T4
Punkty przerwania można ustawiać w szablonach tekstowych. Aby debugować szablon tekstowy czasu projektowania, zapisz plik szablonu tekstowego, a następnie wybierz pozycję Debuguj szablon **T4** w menu skrótów pliku w Eksplorator rozwiązań. Aby debugować szablon tekstowy czasu uruchamiania, wystarczy debugować aplikację, do której należy.

 Aby debugować szablon tekstowy, należy zrozumieć kroki procesu przekształcania szablonu. W każdym kroku mogą wystąpić różne rodzaje błędów. Kroki są następujące.

|Krok|Szablon czasu projektowania: kiedy to się dzieje|Szablon czasu uruchamiania: kiedy to się dzieje|
|-|-|-|
|Kod jest generowany na podstawie szablonu tekstowego.<br /><br /> Błędy w dyrektywach lub niezgodne lub błędne `<#...#>` tagi.|Podczas zapisywania szablonu lub wywoływania przekształcenia tekstu.|Podczas zapisywania szablonu lub wywoływania przekształcenia tekstu.|
|Wygenerowany kod jest kompilowany.<br /><br /> Błędy kompilacji w kodzie szablonu.|Natychmiast po poprzednim kroku.|Wraz z kodem aplikacji.|
|Kod jest uruchamiany.<br /><br /> Błędy czasu uruchamiania w kodzie szablonu.|Natychmiast po poprzednim kroku.|Gdy aplikacja jest uruchamiana i wywołuje kod szablonu.|

 W większości przypadków numery wiersza w kodzie szablonu są podane w raporcie o błędach. Gdy raport o błędach odwołuje się do tymczasowej nazwy pliku, typową przyczyną jest niedopasowany nawias w kodzie szablonu tekstu.

 Punkty przerwania można ustawiać w szablonach tekstowych i debugować w zwykły sposób.

## <a name="common-errors-and-fixes"></a>Typowe błędy i poprawki
 W poniższej tabeli wymieniono najbardziej typowe błędy i ich poprawki.

|Komunikat o błędzie|Opis|Rozwiązanie|
|-|-|-|
|Nie można załadować klasy bazowej {0} "", z której dziedziczy klasa Transformation.|Występuje, jeśli nie można znaleźć klasy bazowej określonej w `inherits` parametrze w dyrektywie szablonu. Komunikat zawiera numer wiersza dyrektywy szablonu.|Upewnij się, że określona klasa istnieje i że zestaw, w nim istnieje, jest określony w dyrektywie zestawu.|
|Nie można rozpoznać dołączanego tekstu dla pliku:{0}|Występuje, gdy nie można znaleźć dołączonego szablonu. Komunikat zawiera nazwę żądanego pliku dołączania.|Upewnij się, że ścieżka pliku jest względna względem oryginalnej ścieżki szablonu lub że plik znajduje się w lokalizacji zarejestrowanej na hoście lub że istnieje pełna ścieżka do pliku.|
|Błędy zostały wygenerowane podczas inicjowania obiektu przekształcenia. Przekształcenie nie zostanie uruchomione.|Występuje, gdy wartość "Initialize()" klasy przekształcania zakończyła się niepowodzeniem lub zwróciła wartość false.|Kod w funkcji Initialize() pochodzi z podstawowej klasy przekształceń określonej w dyrektywie i \<#@template#> z procesorów dyrektyw. Błąd, który spowodował niepowodzenie inicjowania, prawdopodobnie znajduje się na liście błędów. Zbadaj, dlaczego zakończyła się niepowodzeniem. Możesz przyjrzeć się rzeczywisteowi wygenerowanemu kodowi dla polecenia Initialize(), korzystając z procedur debugowania szablonu.|
|Zestawowi " {0} " dla procesora dyrektywy " nie {1} udzielono zestawu uprawnień FullTrust. Tylko zaufane zestawy mogą dostarczać procesory dyrektyw. Procesor dyrektywy nie zostanie załadowany.|Występuje, gdy system nie udziela uprawnień FullTrust do zestawu zawierającego procesor dyrektywy. Komunikat zawiera nazwę zestawu i nazwę procesora dyrektywy.|Upewnij się, że używasz tylko zaufanych zestawów na komputerze lokalnym.|
|Ścieżka " {0} " musi być lokalna dla tego komputera lub części zaufanej strefy.|Występuje, gdy dyrektywa lub dyrektywa zestawu odwołuje się do pliku, który nie znajduje się na komputerze lokalnym lub w strefie zaufanej sieci.|Upewnij się, że katalog, w którym znajdują się dyrektywy lub dyrektywy zestawu, znajduje się w zaufanej strefie. Katalog sieciowy można dodać do zaufanej strefy za pomocą Internet Explorer.|
|Wiele błędów składniowych, takich jak "Nieprawidłowy token "catch" lub "Przestrzeń nazw nie może bezpośrednio zawierać elementów członkowskich"|Zbyt wiele zamykających nawiasów klamrowych w kodzie szablonu. Kompilator myli go z kodem standardowej generacji.|Sprawdź liczbę zamykających nawiasów klamrowych i nawiasów klamrowych wewnątrz ograniczników kodu.|
|Pętle lub instrukcje warunkowe nie zostały skompilowane lub wykonane poprawnie. Na przykład: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Ten kod zawsze wyprowadza wartość i. Tylko "Liczba to:" jest warunkowe.|W języku C# zawsze używaj nawiasów klamrowych, aby otaczać bloki tekstowe osadzone w instrukcjach sterowania.|Dodaj nawiasy klamrowe: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|"Wyrażenie jest zbyt złożone" podczas przetwarzania szablonu czasu projektowania lub kompilowania szablonu środowiska uruchomieniowego (wstępnie przetworzonego).<br /><br /> Visual Studio przestaje działać podczas próby inspekcji kodu wygenerowanego przez szablon środowiska uruchomieniowego.|Blok tekstu jest za długi. T4 konwertuje bloki tekstowe na wyrażenie konkatowania ciągów z jednym literałem ciągu dla każdego wiersza szablonu. Bardzo długie bloki tekstowe mogą przekroć limity rozmiaru kompilatora.|Przerwij długi blok tekstu za pomocą bloku wyrażeń, takiego jak:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Opisy i poprawki ostrzeżeń
 W poniższej tabeli wymieniono najbardziej typowe ostrzeżenia wraz z poprawkami, jeśli są dostępne.

|Komunikat ostrzegawczy|Opis|Rozwiązanie|
|-|-|-|
|Załadowanie pliku dołączanego ' {0} zwróciło ciąg o wartości null lub pusty.|Występuje, gdy dołączony plik szablonu tekstowego jest pusty. Komunikat zawiera nazwę dołączonego pliku.|Usuń dyrektywę include lub upewnij się, że plik zawiera zawartość.|
|Przekształcanie kompilowania:|Dołącza ten ciąg do wszystkich błędów lub ostrzeżeń pochodzących z kompilatora podczas kompilowania przekształcenia. Ten ciąg oznacza, że kompilator zrzucił błąd lub ostrzeżenie.|Jeśli masz problem ze znalezieniem biblioteki DLL, może być konieczne podanie pełnej ścieżki lub w pełni kwalifikowanej silnej nazwy, jeśli biblioteka DLL znajduje się w pamięci GAC.|
|Parametr ' {0} ' już istnieje w dyrektywie . Zduplikowany parametr zostanie zignorowany.|Występuje, gdy parametr jest określony więcej niż raz w dyrektywie. Komunikat zawiera nazwę parametru i numer wiersza dyrektywy.|Usuń specyfikację zduplikowanego parametru.|
|Wystąpił błąd podczas ładowania pliku dołączania {0} "". Dyrektywa include zostanie zignorowana.|Występuje, gdy nie można znaleźć pliku określonego w `include` dyrektywie. Komunikat zawiera nazwę pliku i numer wiersza dyrektywy.|Upewnij się, że plik dołączania znajduje się w tym samym katalogu co oryginalny plik szablonu tekstowego lub w jednym z katalogów dołączania zarejestrowanych na hoście.|
|Dla klasy Transformation określono nieprawidłową klasę bazową. Klasa bazowa musi pochodzić od klasy Microsoft.VisualStudio.TextTemplating.TextTransformation.|Występuje, `inherits` gdy parametr w dyrektywie szablonu określa klasę, która nie dziedziczy z `TextTransformation` klasy . Komunikat zawiera numer wiersza dyrektywy szablonu.|Określ klasę pochodzącą od `TextTransformation` klasy .|
|W dyrektywie "template" określono nieprawidłową kulturę. Kultura musi być w formacie "xx-XX". Zostanie użyta niezmienna kultura.|Występuje, gdy parametr culture w dyrektywie szablonu jest niepoprawnie określony. Komunikat zawiera numer wiersza dyrektywy szablonu.|Zmień parametr culture na prawidłową kulturę w formacie "xx-XX".|
|Nieprawidłowa wartość debugowania {0} ' ' została określona w dyrektywie szablonu. Wartość debugowania musi mieć wartość "true" lub "false". Zostanie użyta wartość domyślna "false".|Występuje, `debug` gdy parametr w dyrektywie szablonu jest niepoprawnie określony. Komunikat zawiera numer wiersza dyrektywy szablonu.|Ustaw parametr debugowania na wartość "true" lub "false".|
|W dyrektywie szablonu określono nieprawidłową wartość hostSpecific {0} '. Parametr HostSpecific musi mieć wartość "true" lub "false". Zostanie użyta wartość domyślna "false".|Występuje, gdy parametr specyficzny dla hosta w `template` dyrektywie jest niepoprawnie określony. Komunikat zawiera numer wiersza dyrektywy szablonu.|Ustaw parametr specyficzny dla hosta na wartość "true" lub "false".|
|W dyrektywie {0} "template" określono nieprawidłowy język "". Język musi być "C#" lub "VB". Zostanie użyta wartość domyślna "C#".|Występuje, gdy w dyrektywie określono `template` nieobsługiwany język. Dozwolone są tylko "C#" lub "VB" (bez uwzględniania liter). Komunikat zawiera numer wiersza dyrektywy szablonu.|Ustaw parametr `language` w dyrektywie szablonu na "C#" lub"VB".|
|W szablonie znaleziono wiele dyrektyw wyjściowych. Wszystkie z oprócz pierwszego zostaną zignorowane.|Występuje, gdy `output` w pliku szablonu określono wiele dyrektyw. Komunikat zawiera numer wiersza zduplikowanej dyrektywy wyjściowej.|Usuń `output` zduplikowane dyrektywy.|
|W szablonie znaleziono wiele dyrektyw szablonu. Wszystkie z oprócz pierwszego zostaną zignorowane. W jednej dyrektywie szablonu należy określić wiele parametrów dyrektywy szablonu.|Występuje w przypadku określenia wielu `template` dyrektyw w pliku szablonu tekstowego (w tym dołączonych plików). Komunikat zawiera numer wiersza dyrektywy zduplikowanego szablonu.|Agregowanie `template` różnych dyrektyw do jednej `template` dyrektywy.|
|Dla dyrektywy o nazwie "" nie określono żadnego {0} procesora. Dyrektywa zostanie zignorowana.|Występuje, jeśli `custom` określisz dyrektywę, ale nie pobędę `processor` atrybutu. Komunikat zawiera nazwę dyrektywy i numer wiersza.|Podaj atrybut `processor` z nazwą procesora dla dyrektywy `directive` .|
|Nie można odnaleźć procesora o {0} nazwie " " dla dyrektywy o nazwie " {1} ". Dyrektywa zostanie zignorowana.|Występuje, gdy system nie może odnaleźć `directive` procesora określonego w `custom` dyrektywie. Komunikat zawiera nazwę dyrektywy, nazwę procesora i numer wiersza dyrektywy.|Ustaw atrybut `processor` w dyrektywie na nazwę procesora dyrektywy.|
|Nie znaleziono {0} wymaganego parametru " " dla dyrektywy {1} "". Dyrektywa zostanie zignorowana.|Występuje, gdy system nie dostarcza wymaganego parametru dyrektywy. Komunikat zawiera nazwę brakującego parametru, nazwę dyrektywy i numer wiersza.|Podaj brakujący parametr.|
|Procesor o nazwie " {0} " nie obsługuje dyrektywy o nazwie " {1} ". Dyrektywa zostanie zignorowana.|Występuje, gdy procesor dyrektywy nie obsługuje dyrektywy. Komunikat zawiera nazwę i numer wiersza dyrektywy, która jest wywłasznia, wraz z nazwą procesora dyrektywy.|Popraw nazwę dyrektywy .|
|Dyrektywa include dla pliku " {0} powoduje nieskończoną pętlę.|Wyświetlane, jeśli określono dyrektywy dołączania cyklicznego (na przykład plik A zawiera plik B, który zawiera plik A).|Nie należy określać dyrektyw dołączania cyklicznego.|
|Uruchamianie przekształcenia:|Dołącza ten ciąg do wszystkich błędów lub ostrzeżeń, które są generowane podczas uruchamiania przekształcenia.|Nie dotyczy.|
|W bloku znaleziono nieoczekiwany tag rozpoczęcia lub końcowy. Upewnij się, że nie wpisano błędnie tagu początku lub końca oraz że w szablonie nie ma żadnych zagnieżdżonych bloków.|Wyświetlany w przypadku nieoczekiwanego błędu \<# or #> . Oznacza to, że jeśli przed nim nie ma \<# after another open tag that has not been closed, or you have a #> niezamkniętego otwartego tagu, Komunikat zawiera numer wiersza niezgodnego tagu.|Usuń niezgodny tag początku lub końca albo użyj znaku ucieczki.|
|Dyrektywa została określona w niewłaściwym formacie. Dyrektywa zostanie zignorowana. Określ dyrektywę w formacie `<#@ name [parametername="parametervalue"]*  #>`|Wyświetlane przez parser, jeśli dyrektywa nie jest określona w poprawnym formacie. Komunikat zawiera numer wiersza nieprawidłowej dyrektywy.|Upewnij się, że wszystkie dyrektywy mają postać `<#@ name [parametername="parametervalue"]*  #>` . Aby uzyskać więcej informacji, zobacz [dyrektywy T4 dotyczące szablonów tekstowych](../modeling/t4-text-template-directives.md).|
|Nie można załadować zestawu " {0} " dla zarejestrowanego procesora dyrektywy " {1} " "<br /><br /> {2}|Występuje, gdy procesor dyrektywy nie może zostać załadowany przez hosta. Komunikat identyfikuje zestaw dostarczony dla procesora dyrektywy i nazwę procesora dyrektywy.|Upewnij się, że procesor dyrektywy jest poprawnie zarejestrowany i że istnieje zestaw.|
|Nie można odnaleźć typu " {0} " w zestawie " " dla {1} zarejestrowanego procesora dyrektywy " " {2} "<br /><br /> {3}|Występuje, gdy nie można załadować typu procesora dyrektywy ze swojego zestawu. Komunikat zawiera nazwę typu, zestawu i procesora dyrektywy.|Vshost znajduje informacje o procesorze dyrektywy (nazwa, zestaw i typ) w rejestrze. Upewnij się, że procesor dyrektywy jest poprawnie zarejestrowany i że typ istnieje w zestawie.|
|Występuje problem podczas ładowania zestawu " {0} "|Występuje, gdy występuje problem podczas ładowania zestawu. Komunikat zawiera nazwę zestawu.|Można określić zestawy do załadowania w dyrektywach \<@#assembly#> i przez procesory dyrektyw. Komunikat o błędzie następujący po tym ciągu powinien dostarczyć więcej danych na temat przyczyny błędu ładowania zestawu.|
|Występuje problem podczas tworzenia i inicjowania procesora dla dyrektywy o nazwie {1} "". Typ procesora to {0} . Dyrektywa zostanie zignorowana.|Występuje, gdy system nie może utworzyć lub zainicjować procesora dyrektywy. Komunikat zawiera nazwę i numer wiersza dyrektywy oraz typ procesora.|Upewnij się, że używasz poprawnego procesora dyrektywy i że procesor dyrektywy ma publiczny konstruktor domyślny. W przeciwnym razie użyj opcji debugowania, aby dowiedzieć się, dlaczego metoda Initialize() procesora dyrektywy nie jest awarii. Aby uzyskać więcej informacji, zobacz [Troubleshooting Text Templates (Rozwiązywanie problemów z szablonami tekstowym).](../modeling/debugging-a-t4-text-template.md)|
|Podczas przetwarzania dyrektywy o nazwie "" został zgłoszony {0} wyjątek.|Występuje, gdy procesor dyrektywy zgłasza wyjątek podczas przetwarzania dyrektywy.|Upewnij się, że parametry procesora dyrektywy są poprawne.|
|Host zrzucił wyjątek podczas próby rozpoznania odwołania do zestawu " {0} ".|Występuje, gdy host zgłasza wyjątek podczas próby rozpoznania odwołania do zestawu. Komunikat zawiera ciąg odwołania do zestawu.|Odwołania do zestawu pochodzą z \<@#assembly#> dyrektyw i procesorów dyrektyw. Upewnij się, że parametr "name" podany w parametrze zestawu jest poprawny.|
|Próba określenia nieobsługiwanej {1} wartości " " for {0} dyrektywy {2}|Występuje przez element RequiresProvidesDirectiveProcessor (wszystkie nasze wygenerowane procesory dyrektyw pochodzą z niego), gdy powiązysz nieobsługiwany argument requires lub provides.|Upewnij się, że nazwy w parach name='value' podanych w parametrach requires i provides są poprawne.|
