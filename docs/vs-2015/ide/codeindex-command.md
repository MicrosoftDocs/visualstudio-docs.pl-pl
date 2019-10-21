---
title: CodeIndex — polecenie | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 070106dc4db0f5200c1346bbbf8c0b653aa104e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619677"
---
# <a name="codeindex-command"></a>Polecenie CodeIndex
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj polecenia **CodeIndex** , aby zarządzać indeksowanie kodu na Team Foundation Server. Na przykład możesz chcieć zresetować indeks, aby naprawić CodeLens informacje, lub wyłączyć indeksowanie, aby zbadać problemy z wydajnością serwera.

 **Wymagane uprawnienia**

 Aby użyć polecenia **CodeIndex** , musisz być członkiem grupy zabezpieczeń **Administratorzy Team Foundation** . Zapoznaj się z informacjami [dotyczącymi uprawnień Team Foundation Server](https://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6).

> [!NOTE]
> Nawet jeśli użytkownik loguje się przy użyciu poświadczeń administracyjnych, należy otworzyć okno wiersza polecenia z podwyższonym poziomem uprawnień, aby uruchomić to polecenie. Należy również uruchomić to polecenie z poziomu aplikacji programu Team Foundation.

## <a name="syntax"></a>Składnia

```
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

#### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|------------------|---------------------|
|`CollectionName`|Określa nazwę kolekcji projektów zespołowych. Jeśli nazwa zawiera spacje, należy ująć ją w cudzysłów, na przykład "Witryna firmy Fabrikam w sieci Web".|
|`CollectionId`|Określa numer identyfikacyjny kolekcji projektów zespołowych.|
|`ServerPath`|Określa ścieżkę do pliku kodu.|

|**Zaznaczyć**|**Opis**|
|----------------|---------------------|
|**/indexingStatus**|Pokaż stan i konfigurację usługi indeksowania kodu.|
|**/setIndexing:** [on &#124; off &#124; keepupOnly]|-    **:** Rozpocznij indeksowanie wszystkich zestawów zmian.<br />-   **wyłączone**: Zatrzymaj indeksowanie wszystkich zestawów zmian.<br />-   **keepupOnly**: Zatrzymaj indeksowanie poprzednio utworzonych zestawów zmian i Rozpocznij indeksowanie tylko nowych zestawów zmian.|
|**/Ignorelist:** [Dodaj &#124; &#124; widok &#124; usuwania pozbyćnia] `ServerPath`<br /><br /> Możesz użyć symbolu wieloznacznego (*) na początku, na końcu lub na obu końcach ścieżki serwerowej.|Określa listę plików kodu i ich ścieżek, które nie mają być indeksowane.<br /><br /> -   **Dodaj**: Dodaj plik, którego nie chcesz zindeksować, do listy plików ignorowanych.<br />-   **Usuń**: Usuń plik, który ma być indeksowany z listy plików ignorowanych.<br />-   **Usuń**z: Wyczyść listę plików ignorowanych i Rozpocznij indeksowanie wszystkich plików.<br />**widok**-   : Zobacz wszystkie pliki, które nie są indeksowane.|
|**/listLargeFiles [/filecount:** `FileCount` **/MinSize:** `MinSize`]|Pokazuje określoną liczbę plików, które przekraczają określony rozmiar w KB. Następnie można użyć opcji **/Ignorelist** , aby wykluczyć te pliki z indeksowania.|
|**/reindexAll**|Wyczyść poprzednio indeksowane dane i uruchom ponownie indeksowanie.|
|**/destroyCodeIndex [/noPrompt]**|Usuń indeks kodu i Usuń wszystkie indeksowane dane. Nie wymaga potwierdzenia w przypadku użycia opcji **/noprompt** .|
|**/temporaryDataSizeLimit**: [view &#124; < `SizeInGBs` > &#124; disable]|Kontrolowanie ilości danych tymczasowych tworzonych przez CodeLens podczas przetwarzania grup zmian. Domyślny limit wynosi 2 GB.<br /><br /> **widok**-   : Pokaż limit bieżącego rozmiaru.<br />-    `SizeInGBs`: Zmień limit rozmiaru.<br />-   **wyłączyć**: Usuń limit rozmiaru.<br /><br /> Ten limit jest sprawdzany przed CodeLens przetwarzania nowej grupy zmian. Jeśli dane tymczasowe przekraczają ten limit, CodeLens zatrzyma przetwarzanie poprzednich zestawów zmian, a nie nowych. CodeLens uruchomi ponownie przetwarzanie po wyczyszczeniu danych i spadnie poniżej tego limitu. Czyszczenie jest uruchamiane automatycznie raz dziennie. Oznacza to, że dane tymczasowe mogą przekroczyć ten limit, dopóki czyszczenie zacznie działać.|
|**/indexHistoryPeriod**: [wyświetl &#124; wszystkie &#124; < `NumberOfMonths` >]|Kontroluj, jak długo ma być indeksowana historia zmian. Ma to wpływ na liczbę CodeLens historii. Domyślny limit to 12 miesięcy. Oznacza to, że CodeLens pokazuje historię zmian tylko w ciągu ostatnich 12 miesięcy.<br /><br /> **widok**-   : Pokaż bieżącą liczbę miesięcy.<br />-   **wszystkie**: Indeksuj całą historię zmian.<br />-    `NumberOfMonths`: Zmień liczbę miesięcy używanych do indeksowania historii zmian.|
|**/CollectionName:** `CollectionName`|Określa nazwę kolekcji projektów zespołowych, na której ma zostać uruchomione polecenie **CodeIndex** . Wymagane, jeśli nie używasz **/CollectionID**.|
|**/collectionId:** `CollectionId`|Określa numer identyfikacyjny kolekcji projektów zespołowych, na której ma zostać uruchomione polecenie **CodeIndex** . Wymagane, jeśli nie używasz **/CollectionName**.|

## <a name="examples"></a>Przykłady

> [!NOTE]
> Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w tym dokumencie są fikcyjne.  Żadne powiązania z rzeczywistymi firmami, organizacjami, produktami, nazwami domen, adresami e-mail, logo, osobami, miejscami lub zdarzeniami nie są zamierzone ani wywnioskowane.

 Aby wyświetlić stan i konfigurację indeksowania kodu:

```
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"
```

 Aby rozpocząć indeksowanie wszystkich zestawów zmian:

```
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"
```

 Aby zatrzymać indeksowanie wcześniej utworzonych grup zmian i rozpocząć indeksowanie tylko nowych zestawów zmian:

```
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"
```

 Aby znaleźć maksymalnie 50 plików o rozmiarze większym niż 10 KB:

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

 Aby wyczyścić poprzednio indeksowane dane i ponownie uruchomić indeksowanie:

```
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"
```

 Aby zapisać całą historię grupy zmian:

```
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"
```

 Aby usunąć limit rozmiaru CodeLens danych tymczasowych i kontynuować indeksowanie niezależnie od rozmiaru danych tymczasowych:

```
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"
```

 Aby usunąć indeks kodu z potwierdzeniem:

```
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"
```

## <a name="see-also"></a>Zobacz też
 [Zarządzanie konfiguracją serwera za pomocą](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) [narzędzia wiersza polecenia TFSCONFIG dla programu TFS](https://msdn.microsoft.com/be8c997a-b97b-4e59-97f5-04db0a601a6c)
