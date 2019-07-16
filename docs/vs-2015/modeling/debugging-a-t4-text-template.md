---
title: Debugowanie szablonu tekstowego T4 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
ms.assetid: 0877fdf2-20bf-42da-b3cc-4c5856b80821
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08e74dbb5fefcdaa0959690c7eb1633bca2a8bc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164579"
---
# <a name="debugging-a-t4-text-template"></a>Debugowanie szablonu tekstowego T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz ustawić punkty przerwania w szablonach tekstowych. Aby debugować szablon tekstowy czasu projektowania, Zapisz plik szablonu tekstu, a następnie wybierz **Debuguj szablon T4** menu skrótów pliku w Eksploratorze rozwiązań. Aby debugować szablonie tekstowym czasu wykonywania, po prostu debugowania aplikacji, do której należy.  
  
 Debugowanie szablonu tekstu, należy zrozumieć kroki proces przekształcania szablonu. Różne rodzaje błędów może wystąpić w każdym kroku. Dostępne są następujące kroki.  
  
|Krok|Szablon czasu projektowania: gdy zdarza się to|Szablon czasu wykonywania: gdy zdarza się to|  
|----------|--------------------------------------------|-----------------------------------------|  
|Kod jest generowany na podstawie szablonu tekstu.<br /><br /> Błędy w dyrektywach, niezgodny lub disordered `<#…#>` tagów.|Podczas zapisywania szablonu lub wywoływanie przekształcenia tekstu.|Podczas zapisywania szablonu lub wywoływanie przekształcenia tekstu.|  
|Wygenerowany kod jest kompilowany.<br /><br /> Błędy kompilacji kodu szablonu.|Bezpośrednio po poprzednim kroku.|Wraz z kodu aplikacji.|  
|Kod jest uruchamiany.<br /><br /> Błędy czasu wykonywania w kodzie szablonu.|Bezpośrednio po poprzednim kroku.|Gdy aplikacja działa i wywołuje kod szablonu.|  
  
 W większości przypadków numery wierszy w kodzie szablonu są podane w raport o błędach. Raport o błędach odwołuje się do nazwy pliku tymczasowego, Najczęstszą przyczyną jest niezgodny nawiasu w kodzie szablonu tekstu.  
  
 Możesz ustawić punkty przerwania w szablonach tekstowych i debugować w zwykły sposób.  
  
## <a name="common-errors-and-fixes"></a>Typowe błędy i poprawki  
 W poniższej tabeli wymieniono najbardziej typowe błędy i ich poprawki.  
  
|Komunikat o błędzie|Opis|Rozwiązanie|  
|-------------------|-----------------|--------------|  
|Nie można załadować klasy bazowej{0}"przekształcenia, które klasa dziedziczy.|Występuje, gdy nie można znaleźć klasy bazowej, określone w `inherits` parametru w dyrektywie szablonu. Komunikat zawiera numer wiersza — dyrektywa szablonu.|Upewnij się, określonej klasy istnieje i że zestaw, który znajduje się w określono w dyrektywie zestawu.|  
|Nie można rozpoznać zawierają tekst dla pliku:{0}|Występuje, gdy nie można odnaleźć dołączone szablonu. Komunikat zawiera nazwę żądanej dołączanego pliku.|Pamiętaj, że ścieżka pliku jest względną ścieżkę oryginalnego szablonu lub że plik znajduje się w lokalizacji, która jest zarejestrowana z hostem lub czy jest pełną ścieżką do pliku.|  
|Wygenerowano błędy podczas inicjowania obiektu transformacji. Transformacja nie zostanie uruchomiona.|Występuje, gdy "Initialize()" klasy przekształcenia nie powiodło się lub zwrócił wartość false.|Kod do funkcji Initialize() pochodzi z klasy bazowej przekształcania określonej w \<#@template#> dyrektywy i procesorów dyrektyw. Błąd, który spowodował zainicjować się prawdopodobnie niepowodzeniem znajduje się na liście błędów. Należy zbadać, dlaczego nie powiodło się. Można wyszukać w rzeczywistych wygenerowanego kodu Initialize() zgodnie z instrukcjami opisanymi na debugowanie szablonu.|  
|Zestaw "{0}"dla procesora dyrektywy"{1}" nie uzyskał zestawu uprawnień FullTrust. Tylko zaufane zestawy mogą dostarczać procesory dyrektywy. Procesor dyrektywy nie zostanie załadowany.|Występuje, gdy system nie powoduje przyznania uprawnień FullTrust do zestawu zawierającego procesora dyrektywy. Komunikat zawiera nazwę zestawu i nazwa procesora dyrektywy.|Należy upewnić się, że tylko zaufane zestawy na komputerze lokalnym.|  
|Ścieżka "{0}" musi być lokalną na tym komputerze lub częścią Twojej zaufanej strefy.|Występuje, gdy dyrektywy lub dyrektywa zestawu odwołuje się do pliku, który jest nie na komputerze lokalnym lub w sieci zaufanej strefy.|Pamiętaj, że katalog, w którym dyrektywy lub dyrektyw zestawu znajdują się znajduje się w Twojej zaufanej strefy. Można dodać katalogu sieciowego do zaufanej strefy za pomocą programu Internet Explorer.|  
|Wiele błędów składni, np. "Nieprawidłowy token" catch"" lub "przestrzeni nazw nie może bezpośrednio zawierać składowych"|Zbyt wiele zamykające nawiasy klamrowe w kodzie szablonu. Kompilator jest skomplikowana go przy użyciu kodu generacja standard.|Sprawdź numer zamykające nawiasy i nawiasy kwadratowe wewnątrz kodu ograniczników.|  
|Pętle warunkowych nie skompilowany lub wykonywane poprawnie. Na przykład: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Ten kod zawsze wyświetla wartość i. Tylko "Liczba to:" to warunkowe.|W języku C# należy zawsze używać nawiasów klamrowych otoczyć bloków tekstu, które są osadzone w instrukcjach sterowania.|Dodaj nawiasy klamrowe: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|"Wyrażenie jest zbyt złożone" podczas przetwarzania szablonu projektowania lub skompilowanie szablonu (wstępnie przetworzony) czasu wykonywania.<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przestaje działać podczas próby sprawdź kod wygenerowany przez szablonów czasu wykonywania.|Blok tekstu jest za długa. T4 konwertuje wyrażenie łączenia ciągu przy użyciu jednego ciągu literału dla każdego wiersza szablonu bloki tekstu. Bloki bardzo długie teksty można przekroczyć limitów rozmiarów kompilatora.|Podziel bloku długie teksty z bloku wyrażenia takie jak:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Ostrzeżenie opisy i poprawki  
 W poniższej tabeli wymieniono najbardziej typowe ostrzeżenia wraz z poprawek, jeśli jest dostępny.  
  
|Komunikat ostrzegawczy|Opis|Rozwiązanie|  
|---------------------|-----------------|--------------|  
|Podczas ładowania pliku dyrektywy include "{0}" zwrócił wartość null lub pusty ciąg.|Występuje, gdy plik szablonu dołączonym tekście jest pusta. Komunikat zawiera nazwę pliku dołączonego pliku.|Usuń dyrektywy include lub upewnij się, że plik ma odpowiednią zawartość.|  
|Kompilowanie transformacji:|Dołącza ten ciąg do wszystkich ostrzeżeń ani błędów, pochodzące z kompilatora, jeżeli kompiluje transformacji. Ten ciąg oznacza, że kompilator wygenerował błąd lub ostrzeżenie.|Jeśli masz problem ze znalezieniem biblioteki DLL, może być konieczne Podaj pełną ścieżkę lub pełną silnej nazwy, jeśli biblioteka DLL jest w GAC.|  
|Parametr "{0}" już istnieje w dyrektywie. Zduplikowany parametr zostanie zignorowany.|Występuje, gdy parametr jest określony więcej niż jeden raz w dyrektywie. Komunikat zawiera nazwę parametru i numer wiersza dyrektywy.|Usuń specyfikację zduplikowany parametr.|  
|Wystąpił błąd podczas ładowania pliku dyrektywy include "{0}". Dyrektywa include zostaną zignorowane.|Występuje, gdy nie można odnaleźć pliku określonego w `include` dyrektywy. Komunikat zawiera nazwę pliku i numer wiersza dyrektywy.|Upewnij się, że istnieje dołączanego pliku, w tym samym katalogu co oryginalny plik szablonu tekstu lub w jednym z katalogów dołączanych, które są zarejestrowane z hostem.|  
|Określono nieprawidłową klasę bazową klasy przekształcenia. Klasa bazowa musi pochodzić od element Microsoft.VisualStudio.TextTemplating.TextTransformation.|Występuje, gdy `inherits` parametr w dyrektywie szablonu określa klasę, która dziedziczy `TextTransformation`. Komunikat zawiera numer wiersza — dyrektywa szablonu.|Określ klasę, która pochodzi od klasy `TextTransformation`.|  
|Określono nieprawidłową kulturę w dyrektywie "template". Kultura musi mieć format "xx-XX". Zostanie użyta kultura niezmienna.|Występuje, gdy parametr kulturę w dyrektywie szablonu została określona nieprawidłowo. Komunikat zawiera numer wiersza — dyrektywa szablonu.|Zmień wartość parametru kultury prawidłową kulturą format "xx-XX".|  
|Nieprawidłową wartość debugowania "{0}" został określony w dyrektywie szablonu. Wartość debugowania musi być "true" lub "false". Wartość domyślna "false" będą używane.|Występuje, gdy `debug` nieprawidłowo określono parametr w dyrektywie szablonu. Komunikat zawiera numer wiersza — dyrektywa szablonu.|Ustaw parametr debugowania na "true" lub "false".|  
|Nieprawidłowa wartość HostSpecific "{0}" został określony w dyrektywie szablonu. Wartość HostSpecific musi być "true" lub "false". Wartość domyślna "false" będą używane.|Występuje, gdy parametr specyficzne dla hosta w `template` dyrektywa została określona nieprawidłowo. Komunikat zawiera numer wiersza — dyrektywa szablonu.|Ustaw parametr specyficzne dla hosta na "true" lub "false".|  
|Nieprawidłowy język "{0}" został określony w dyrektywie "template". Język musi być "C#" lub "VB". Wartość domyślna "C#" będą używane.|Występuje, gdy określono nieobsługiwany język w `template` dyrektywy. Tylko "C#" lub "VB" są dozwolone (wielkich liter). Komunikat zawiera numer wiersza — dyrektywa szablonu.|Ustaw `language` parametru w dyrektywie szablonu, "C#" lub "VB".|  
|W szablonie znaleziono wiele dyrektyw danych wyjściowych. Wszystkie oprócz pierwszej zostaną zignorowane.|Występuje, gdy wiele `output` dyrektywy są określone w pliku szablonu. Komunikat zawiera numer wiersza dyrektywy zduplikowany wyjściowy.|Usuń zduplikowane `output` dyrektywy.|  
|W szablonie znaleziono wiele dyrektyw template. Wszystkie oprócz pierwszej zostaną zignorowane. W ramach jednej dyrektywy template należy określić wiele parametrów dyrektywy template.|Występuje, jeśli określisz wiele `template` dyrektywy w pliku szablonu tekstu (w tym uwzględnione pliki). Komunikat zawiera numer wiersza dyrektywy duplikat szablonu.|Agreguj różnych `template` dyrektywy do jednego `template` dyrektywy.|  
|Nie określono procesora dla dyrektywy o nazwie "{0}". Dyrektywa zostanie zignorowana.|Występuje, jeśli określisz `custom` dyrektywy, ale nie zapewniają `processor` atrybutu. Komunikat zawiera nazwę dyrektywy i numer wiersza.|Podaj `processor` atrybutu o nazwie `directive` procesora dla dyrektywy.|  
|Procesor o nazwie "{0}"nie można odnaleźć dla dyrektywy o nazwie"{1}". Dyrektywa zostanie zignorowana.|Występuje, gdy system nie może odnaleźć `directive` procesora, określone w `custom` dyrektywy. Komunikat zawiera nazwy dyrektywy, procesor nazwę i numer wiersza dyrektywy.|Ustaw `processor` atrybutu w dyrektywie do nazwy procesora dyrektywy.|  
|Wymagany parametr "{0}"dla dyrektywy"{1}" nie został znaleziony. Dyrektywa zostanie zignorowana.|Występuje, gdy system nie zawiera wymaganego parametru dyrektywy. Komunikat zawiera nazwę brakującego parametru, dyrektywy nazwę i numer wiersza.|Podaj brakującego parametru.|  
|Procesor o nazwie "{0}"nie obsługuje dyrektywy o nazwie"{1}". Dyrektywa zostanie zignorowana.|Występuje, gdy procesor dyrektywy nie obsługuje dyrektywy. Komunikat zawiera nazwę i numer wiersza naruszającym dyrektywy wraz z nazwą procesora dyrektywy.|Popraw nazwę dyrektywy.|  
|Dyrektywa include dla pliku "{0}" powoduje nieskończoną pętlę.|Wyświetlane, gdy dyrektywy #include cykliczne są określone (na przykład plik A zawiera plik B, który zawiera plik, A).|Nie określaj cykliczne dyrektywy #include.|  
|Uruchamianie transformacji:|Dołącza ten ciąg, aby wszystkie błędy lub ostrzeżenia, które są generowane podczas wykonywania przekształcenia.|Nie dotyczy.|  
|Nieoczekiwany tag początkowy lub końcowy został znaleziony w bloku. Upewnij się, że użytkownik został poprawnie wpisany tag początkowy lub końcowy i że nie masz wszelkich bloków zagnieżdżonych w szablonie.|Wyświetlane, gdy użytkownik ma nieoczekiwany \<# lub #>. Oznacza to jeśli masz \<# po tagu Otwórz inny, które nie zostały zamknięte, albo masz #> po nie zamknięto tagu open przed nią. Komunikat zawiera numer wiersza niedopasowanych tagu.|Usuń niezgodnego tag początkowy lub końcowy lub użyj znaku ucieczki.|  
|Dyrektywa został określona w nieprawidłowym formacie. Dyrektywa zostanie zignorowana. Określ dyrektywę w formacie `<#@ name [parametername="parametervalue"]*  #>`|Wyświetlane przez analizator, jeśli nie określono dyrektywy w poprawnym formacie. Komunikat zawiera numer wiersza niepoprawne dyrektywy.|Pamiętaj, że wszystkie dyrektywy znajdują się w formularzu `<#@ name [parametername="parametervalue"]*  #>`. Aby uzyskać więcej informacji, zobacz [dyrektywy T4 dotyczące szablonu tekstowego](../modeling/t4-text-template-directives.md).|  
|Nie można załadować zestawu "{0}"dla zarejestrowanego procesora dyrektywy"{1}"<br /><br /> {2}|Występuje, gdy procesor dyrektywy nie mógł zostać załadowany przez hosta. Komunikat identyfikuje zestaw przewidzianej do procesora dyrektywy i nazwę procesor dyrektywy.|Upewnij się procesor dyrektywy jest poprawnie zarejestrowany oraz że ten zestaw istnieje.|  
|Nie można odnaleźć typu "{0}"w zestawie"{1}"dla zarejestrowanego procesora dyrektywy"{2}"<br /><br /> {3}|Występuje, gdy nie można załadować typu procesora dyrektywy z własnego zestawu. Komunikat zawiera nazwę typu, zestawu i procesora dyrektywy.|Vshost umożliwia znalezienie informacji procesor dyrektywy (nazwa zestawu i typu) w rejestrze. Upewnij się, procesor dyrektywy jest poprawnie zarejestrowany i czy typ istnieje w zestawie.|  
|Wystąpił problem podczas ładowania zestawu "{0}"|Występuje, gdy występuje problem z ładowaniem zestawu. Komunikat zawiera nazwę zestawu.|Można określić zestawy, aby można było załadować \<@# assembly #> dyrektyw oraz przez procesory dyrektyw. Komunikat o błędzie, występującego ciąg ten powinien zapewnić większej ilości danych na Dlaczego nie można załadować zestawu.|  
|Wystąpił problem podczas tworzenia i inicjowania procesora dla dyrektywy o nazwie "{1}". Typ procesora jest {0}. Dyrektywa zostanie zignorowana.|Występuje, gdy system nie można utworzyć lub zainicjować procesor dyrektywy. Komunikat zawiera nazwę i numer wiersza dyrektywy i typ procesora.|Upewnij się, użyj poprawne procesora dyrektywy i że procesor dyrektywy ma publicznego konstruktora domyślnego. W przeciwnym razie użyj opcji debugowania, aby dowiedzieć się, dlaczego metody Initialize() procesor dyrektywy nie działa prawidłowo. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z szablonów tekstowych](../modeling/debugging-a-t4-text-template.md).|  
|Wystąpił wyjątek podczas przetwarzania dyrektywy o nazwie "{0}".|Występuje, gdy procesor dyrektywy zgłasza wyjątek podczas przetwarzania dyrektywy.|Pamiętaj, że parametry do procesora dyrektywy są poprawne.|  
|Host zgłosił wyjątek podczas próby rozpoznania odwołania do zestawu "{0}".|Występuje, gdy host zgłasza wyjątek, gdy próbuje rozpoznać odwołania do zestawu. Komunikat zawiera zestaw odwoływać się do ciągu.|Zestaw odwołania pochodzą \<@# assembly #> dyrektyw i procesorów dyrektyw. Pamiętaj, że parametr "name" podana w parametrze zestawu jest poprawny.|  
|Próba określenia nieobsługiwany {1} wartość "{0}" dla dyrektywy {2}|Wykonywane przez RequiresProvidesDirectiveProcessor, (wszystkie nasze wygenerowane procesory dyrektyw dziedziczyć po nim), podczas dostarczania nieobsługiwana dostarczania lub wymagania argumentu.|Pamiętaj, że nazwy w name = 'value' par w wymaga i zawiera parametry są poprawne.|
