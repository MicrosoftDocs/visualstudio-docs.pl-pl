---
title: Polecenie CodeIndex | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f16d21889421a00fc2723412f34b426f75847822
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701622"
---
# <a name="codeindex-command"></a>Polecenie CodeIndex
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **CodeIndex** polecenia do zarządzania indeksowaniem kodu na serwerze Team Foundation Server. Na przykład można zresetować indeks, aby naprawić informacje narzędzia CodeLens, lub wyłączyć indeksowanie, aby zbadać problemy z wydajnością serwera.  
  
 **Wymagane uprawnienia**  
  
 Aby użyć **CodeIndex** polecenia, musi być członkiem **Administratorzy Team Foundation** grupy zabezpieczeń. Zobacz [odwołania uprawnień dla serwera Team Foundation Server](https://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6).  
  
> [!NOTE]
> Nawet wtedy, gdy użytkownik loguje się przy użyciu poświadczeń administracyjnych, należy otworzyć podwyższone okno Wiersz polecenia, aby uruchomić to polecenie. Należy także uruchomić to polecenie z warstwy aplikacji programu Team Foundation.  
  
## <a name="syntax"></a>Składnia  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|**Argument**|**Opis**|  
|------------------|---------------------|  
|`CollectionName`|Określa nazwę kolekcji projektu zespołowego. Jeśli nazwa zawiera spacje, należy ją ująć w cudzysłów, na przykład "Fabrikam Web Site".|  
|`CollectionId`|Określa numer identyfikujący kolekcji projektu zespołowego.|  
|`ServerPath`|Określa ścieżkę do pliku kodu.|  
  
|**Option**|**Opis**|  
|----------------|---------------------|  
|**/indexingStatus**|Pokazuje stan i konfigurację usługi indeksowania kodu.|  
|**/setIndexing:**[na &#124; poza &#124; keepupOnly]|-   **on**: Uruchom indeksowanie wszystkich zestawów zmian.<br />-   **off**: Zatrzymaj indeksowanie wszystkich zestawów zmian.<br />-   **keepupOnly**: Zatrzymaj indeksowanie utworzonych wcześniej zestawów zmian i Rozpocznij indeksowanie tylko nowych zestawów zmian.|  
|**/ignoreList:**[Dodaj &#124; Usuń &#124; removeAll &#124; view] `ServerPath`<br /><br /> Można użyć znaku wieloznacznego (*) na początku, zakończenia lub obu końcach ścieżki serwera.|Określa listę plików kodu i ich ścieżek, które nie mają być indeksowane.<br /><br /> -   **Dodaj**: Dodaj plik, który ma nie być indeksowane do listy plików ignorowanych.<br />-   **remove**: Usuń plik, który ma być indeksowane z listy plików ignorowanych.<br />-   **removeAll**: Wyczyść listę ignorowanych plików i Rozpocznij indeksowanie wszystkich plików.<br />-   **Widok**: Zobacz wszystkie pliki, które nie są indeksowane.|  
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Przedstawia określoną liczbę plików, która przekracza określony rozmiar w KB. Następnie można użyć **/ignoreList** opcji, aby wykluczyć te pliki z indeksowania.|  
|**/reindexAll**|Wyczyść wcześniej zaindeksowane dane i ponownie uruchom indeksowanie.|  
|**/destroyCodeIndex [/noPrompt]**|Usuń indeks kodu i wszystkie indeksowane dane. Nie wymaga potwierdzenia, jeśli używasz **/noprompt** opcji.|  
|**/temporaryDataSizeLimit**: [widok &#124; <`SizeInGBs`> &#124; wyłączone]|Kontrolowanie ile tymczasowe dane CodeLens tworzy podczas przetwarzania zmian. Domyślny limit wynosi 2 GB.<br /><br /> -   **Widok**: Pokaż bieżący limit rozmiaru.<br />-   `SizeInGBs`: Zmień limit rozmiaru.<br />-   **disable**: Usuń limit rozmiaru.<br /><br /> Ten limit jest sprawdzany przed CodeLens przetwarza nowy zestaw zmian. Jeśli dane tymczasowe przekracza ten limit, CodeLens spowoduje wstrzymanie przetwarzania ostatnie zestawy zmian, nie nowe. Funkcja CodeLens spowoduje ponowne uruchomienie przetwarzania po danych jest wyczyszczone, a spadnie poniżej tego limitu. Czyszczenie jest uruchamiany automatycznie raz dziennie. Oznacza to, że dane tymczasowe może przekroczyć tego limitu, dopóki oczyszczania zacznie działać.|  
|**/indexHistoryPeriod**: [widok &#124; wszystkich &#124; <`NumberOfMonths`>]|Formant, jak długo indeksu historię zmian. Dotyczy to, ile historii CodeLens pokazuje. Domyślny limit to 12 miesięcy. Oznacza to rozwiązanie CodeLens Pokazuje historię zmian z ostatnich 12 miesięcy tylko.<br /><br /> -   **Widok**: Pokaż bieżącą liczbę miesięcy.<br />-   **wszystkie**: Indeks wszystkich historii zmian.<br />-   `NumberOfMonths`: Zmień liczbę miesięcy, używany do historii zmian indeksu.|  
|**/collectionName:** `CollectionName`|Określa nazwę kolekcji projektu zespołowego, na którym ma być uruchamiany **CodeIndex** polecenia. Wymagane, jeśli nie używasz **/CollectionId**.|  
|**/collectionId:** `CollectionId`|Określa numer identyfikujący kolekcji projektu zespołowego, na którym ma być uruchamiany **CodeIndex** polecenia. Wymagane, jeśli nie używasz **/CollectionName**.|  
  
## <a name="examples"></a>Przykłady  
  
> [!NOTE]
> Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w niniejszym dokumencie są fikcyjne.  Wszelkie rzeczywistą firmą, organizacji, produktu, nazwy domeny, adres e-mail, logo, osoby, miejsca lub zdarzeń jest przeznaczone i powinno być wnioskowane.  
  
 Aby zobaczyć status indeksowania kodu i konfiguracji:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Aby rozpocząć indeksowanie wszystkich zestawów zmian:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Aby zatrzymać indeksowanie wcześniej utworzonych zestawów zmian i Rozpocznij indeksowanie tylko nowych zestawów zmian:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 Aby znaleźć do 50 plików, które są większe niż 10 KB:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Aby wykluczyć określony plik z indeksowania i dodać go do listy plików ignorowanych:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Aby wyświetlić wszystkie pliki, które nie są indeksowane:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Aby wyczyścić wcześniej indeksowane dane i ponownie uruchomić indeksowanie:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Aby zapisać całą historię zmian:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Aby usunąć limit rozmiaru danych tymczasowych CodeLens i kontynuować indeksowanie niezależnie od rozmiaru danych tymczasowych:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Aby usunąć indeks kodu z potwierdzeniem:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie konfiguracją serwera za pomocą TFSConfig](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [Narzędzia wiersza polecenia dla TFS](https://msdn.microsoft.com/be8c997a-b97b-4e59-97f5-04db0a601a6c)
