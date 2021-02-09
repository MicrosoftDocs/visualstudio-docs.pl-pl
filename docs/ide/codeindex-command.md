---
title: CodeIndex — polecenie
description: Dowiedz się, jak za pomocą polecenia CodeIndex zarządzać indeksem kodu na Azure DevOps Server (wcześniej znanym jako Team Foundation Server).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47875bcece910433a1d20ad66867acd7fdbee8d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841928"
---
# <a name="codeindex-command"></a>CodeIndex — polecenie

Użyj polecenia **CodeIndex** , aby zarządzać indeksowanie kodu na Team Foundation Server. Na przykład możesz chcieć zresetować indeks, aby naprawić CodeLens informacje, lub wyłączyć indeksowanie, aby zbadać problemy z wydajnością serwera.

## <a name="required-permissions"></a>Wymagane uprawnienia

Aby użyć polecenia **CodeIndex** , musisz być członkiem grupy zabezpieczeń **Administratorzy Team Foundation** . Zobacz [uprawnienia i grupy zdefiniowane dla Azure DevOps Services i TFS](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true).

> [!NOTE]
> Nawet jeśli użytkownik loguje się przy użyciu poświadczeń administracyjnych, należy otworzyć okno wiersza polecenia z podwyższonym poziomem uprawnień, aby uruchomić to polecenie. Należy również uruchomić to polecenie z poziomu aplikacji programu Team Foundation.

## <a name="syntax"></a>Składnia

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|------------------| - |
|`CollectionName`|Określa nazwę kolekcji projektu. Jeśli nazwa zawiera spacje, należy ująć ją w cudzysłów, na przykład "Witryna sieci Web firmy Fabrikam".|
|`CollectionId`|Określa numer identyfikacyjny kolekcji projektu.|
|`ServerPath`|Określa ścieżkę do pliku kodu.|

|**Opcja**|**Opis**|
|----------------| - |
|**/indexingStatus**|Pokaż stan i konfigurację usługi indeksowania kodu.|
|**/setIndexing:**[on &#124; off &#124; keepupOnly]|-   **włączone**: Rozpocznij indeksowanie wszystkich zestawów zmian.<br />-   **wyłączone**: Zatrzymaj indeksowanie wszystkich zestawów zmian.<br />-   **keepupOnly**: Zatrzymaj indeksowanie wcześniej utworzonych zestawów zmian i Rozpocznij indeksowanie tylko nowych zestawów zmian.|
|**/Ignorelist:**[Dodaj &#124; usuń &#124; &#124; widok `ServerPath`<br /><br /> Możesz użyć symbolu wieloznacznego (*) na początku, na końcu lub na obu końcach ścieżki serwerowej.|Określa listę plików kodu i ich ścieżek, które nie mają być indeksowane.<br /><br /> -   **Dodaj**: Dodaj plik, którego nie chcesz zindeksować, do listy plików ignorowanych.<br />-   **Usuń**: Usuń plik, który ma być indeksowany z listy plików ignorowanych.<br />-   Usuń z listy ignorowanych plików i Rozpocznij indeksowanie wszystkich plików.<br />-   **Widok**: Zobacz wszystkie pliki, które nie są indeksowane.|
|**/listLargeFiles [/filecount:** `FileCount` **/MinSize:** `MinSize` ]|Pokazuje określoną liczbę plików, które przekraczają określony rozmiar w KB. Następnie można użyć opcji **/Ignorelist** , aby wykluczyć te pliki z indeksowania.|
|**/reindexAll**|Wyczyść poprzednio indeksowane dane i uruchom ponownie indeksowanie.|
|**/destroyCodeIndex [/noPrompt]**|Usuń indeks kodu i Usuń wszystkie indeksowane dane. Nie wymaga potwierdzenia w przypadku użycia opcji **/noprompt** .|
|**/temporaryDataSizeLimit**: [wyświetl &#124; <`SizeInGBs`> &#124; wyłączyć]|Kontrolowanie ilości danych tymczasowych tworzonych przez CodeLens podczas przetwarzania grup zmian. Domyślny limit wynosi 2 GB.<br /><br /> -   **Widok**: pokazuje bieżący limit rozmiaru.<br />-   `SizeInGBs`: Zmień limit rozmiaru.<br />-   **Wyłącz**: Usuń limit rozmiaru.<br /><br /> Ten limit jest sprawdzany przed CodeLens przetwarzania nowej grupy zmian. Jeśli dane tymczasowe przekraczają ten limit, CodeLens zatrzyma przetwarzanie poprzednich zestawów zmian, a nie nowych. CodeLens uruchomi ponownie przetwarzanie po wyczyszczeniu danych i spadnie poniżej tego limitu. Czyszczenie jest uruchamiane automatycznie raz dziennie. Oznacza to, że dane tymczasowe mogą przekroczyć ten limit, dopóki czyszczenie zacznie działać.|
|**/indexHistoryPeriod**: [widok &#124; wszystkie &#124; <`NumberOfMonths`>]|Kontroluj, jak długo ma być indeksowana historia zmian. Ma to wpływ na liczbę CodeLens historii. Domyślny limit to 12 miesięcy. Oznacza to, że CodeLens pokazuje historię zmian tylko w ciągu ostatnich 12 miesięcy.<br /><br /> -   **Widok**: pokazuje bieżącą liczbę miesięcy.<br />-   **wszystkie**: Indeksuj całą historię zmian.<br />-   `NumberOfMonths`: Zmień liczbę miesięcy używanych do indeksowania historii zmian.|
|**/CollectionName:**`CollectionName`|Określa nazwę kolekcji projektu, na której ma zostać uruchomione polecenie **CodeIndex** . Wymagane, jeśli nie używasz **/CollectionID**.|
|**/collectionId:**`CollectionId`|Określa numer identyfikacyjny kolekcji projektów, na której ma zostać uruchomione polecenie **CodeIndex** . Wymagane, jeśli nie używasz **/CollectionName**.|

## <a name="examples"></a>Przykłady

> [!NOTE]
> Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia wymienione w tym dokumencie są fikcyjne.  Żadne powiązania z rzeczywistymi firmami, organizacjami, produktami, nazwami domen, adresami e-mail, logo, osobami, miejscami lub zdarzeniami nie są zamierzone ani wywnioskowane.

Aby wyświetlić stan i konfigurację indeksowania kodu:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Aby rozpocząć indeksowanie wszystkich zestawów zmian:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Aby zatrzymać indeksowanie wcześniej utworzonych grup zmian i rozpocząć indeksowanie tylko nowych zestawów zmian:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

Aby znaleźć maksymalnie 50 plików o rozmiarze większym niż 10 KB:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Aby wykluczyć określony plik z indeksowania i dodać go do listy plików ignorowanych:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Aby wyświetlić wszystkie pliki, które nie są indeksowane:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Aby wyczyścić poprzednio indeksowane dane i ponownie uruchomić indeksowanie:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Aby zapisać całą historię grupy zmian:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

Aby usunąć limit rozmiaru CodeLens danych tymczasowych i kontynuować indeksowanie niezależnie od rozmiaru danych tymczasowych:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Aby usunąć indeks kodu z potwierdzeniem:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Zarządzanie konfiguracją serwera za pomocą polecenia TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd)
