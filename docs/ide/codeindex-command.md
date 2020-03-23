---
title: Polecenie CodeIndex
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bd2a6cc947c5f52212029bebe590d59906f5aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591167"
---
# <a name="codeindex-command"></a>Polecenie CodeIndex

Polecenie **CodeIndex** służy do zarządzania indeksowania kodu na serwerze Team Foundation Server. Na przykład można zresetować indeks, aby naprawić informacje CodeLens lub wyłączyć indeksowanie w celu zbadania problemów z wydajnością serwera.

## <a name="required-permissions"></a>Wymagane uprawnienia

Aby użyć polecenia **CodeIndex,** musisz być członkiem grupy zabezpieczeń **Administratorzy fundacji zespołu.** Zobacz [Uprawnienia i grupy zdefiniowane dla usług Azure DevOps services i TFS](/azure/devops/organizations/security/permissions?view=vsts).

> [!NOTE]
> Nawet jeśli zalogujesz się przy użyciu poświadczeń administracyjnych, musisz otworzyć okno wiersza polecenia z podwyższonym poziomem uprawnień, aby uruchomić to polecenie. Należy również uruchomić to polecenie z warstwy aplikacji dla Team Foundation.

## <a name="syntax"></a>Składnia

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|------------------| - |
|`CollectionName`|Określa nazwę kolekcji projektu. Jeśli nazwa zawiera spacje, należy ująć nazwę ze znakami cudzysłowu, na przykład "Fabrikam Website".|
|`CollectionId`|Określa numer identyfikacyjny kolekcji projektu.|
|`ServerPath`|Określa ścieżkę do pliku kodu.|

|**Opcja**|**Opis**|
|----------------| - |
|**/indexingStatus**|Pokaż stan i konfigurację usługi indeksowania kodu.|
|**/setIndexing:**[ na &#124; wyłączony &#124; keepupOnly ]|-   **on**: Rozpocznij indeksowanie wszystkich zmian.<br />-   **off**: Przestań indeksować wszystkie zestawy zmian.<br />-   **keepupOnly**: Zatrzymaj indeksowanie wcześniej utworzonych wichli zmian i zacznij indeksować tylko nowe zestawy zmian.|
|**/ignoreList:**[ dodaj &#124; usuń &#124; removeWszystki widok &#124; ]`ServerPath`<br /><br /> Symbol wieloznaczny (*) można użyć na początku, końcu lub na obu końcach ścieżki serwera.|Określa listę plików kodu i ich ścieżek, które nie mają być indeksowane.<br /><br /> -   **dodaj**: Dodaj plik, który nie ma być indeksowany do listy ignorowanych plików.<br />-   **usuń**: Usuń plik, który chcesz zaindeksować z listy ignorowanych plików.<br />-   **removeAll**: Wyczyść listę ignorowanych plików i zacznij indeksować wszystkie pliki.<br />-   **view**: Zobacz wszystkie pliki, które nie są indeksowane.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Pokazuje określoną liczbę plików, która przekracza określony rozmiar w KB. Następnie można użyć **/ignoreList** opcji, aby wykluczyć te pliki z indeksowania.|
|**/reindexWszystki**|Wyczyść wcześniej indeksowane dane i uruchom ponownie indeksowanie.|
|**/destroyCodeIndex [/noPrompt]**|Usuń indeks kodu i usuń wszystkie dane indeksowane. Nie wymaga potwierdzenia, jeśli używasz opcji **/noPrompt.**|
|**/temporaryDataSizeLimit**:[ view `SizeInGBs` &#124; <> &#124; disable ]|Osłanianie ilości tymczasowych danych, które codelens tworzy podczas przetwarzania zestawów zmian. Domyślny limit wynosi 2 GB.<br /><br /> -   **view**: Pokaż bieżący limit rozmiaru.<br />-   `SizeInGBs`: Zmień limit rozmiaru.<br />-   **disable**: Usuń limit rozmiaru.<br /><br /> Ten limit jest sprawdzany przed CodeLens przetwarza nowy zestawy zmian. Jeśli dane tymczasowe przekroczą ten limit, CodeLens wstrzyma przetwarzanie wcześniejszych zestawów zmian, a nie nowych. CodeLens uruchomi ponowne przetwarzanie po wyczyszczeniu danych i spadnie poniżej tego limitu. Oczyszczanie jest uruchamiane automatycznie raz dziennie. Oznacza to, że dane tymczasowe mogą przekroczyć ten limit, dopóki oczyszczanie nie zacznie działać.|
|**/indexHistoryPeriod**:[ zobacz &#124; wszystkie &#124; <`NumberOfMonths`> ]|Kontroluj, jak długo chcesz indeksować historię zmian. Wpływa to na to, ile historii CodeLens pokazuje. Domyślny limit wynosi 12 miesięcy. Oznacza to, że codelens pokazuje historię zmian tylko z ostatnich 12 miesięcy.<br /><br /> -   **view**: Pokaż bieżącą liczbę miesięcy.<br />-   **wszystkie**: Indeks wszystkie historii zmian.<br />-   `NumberOfMonths`: Zmiana liczby miesięcy używanych do indeksu historii zmian.|
|**/collectionName:**`CollectionName`|Określa nazwę kolekcji projektu, na której ma być uruchamiane polecenie **CodeIndex.** Wymagane, jeśli nie używasz **/CollectionId**.|
|**/collectionId:**`CollectionId`|Określa numer identyfikacyjny kolekcji projektu, na którym ma być uruchamiane polecenie **CodeIndex.** Wymagane, jeśli nie używasz **/CollectionName**.|

## <a name="examples"></a>Przykłady

> [!NOTE]
> Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i wydarzenia przedstawione w niniejszym dokumencie są fikcyjne.  Żadne skojarzenia z jakąkolwiek rzeczywistą firmą, organizacją, produktem, nazwą domeny, adresem e-mail, logo, osobą, miejscami lub wydarzeniami nie są zamierzone ani nie powinny być wywnioskowane.

Aby wyświetlić stan i konfigurację indeksowania kodu:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Aby rozpocząć indeksowanie wszystkich zmian:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Aby zatrzymać indeksowanie wcześniej utworzonych wichury zmian i rozpocząć indeksowanie tylko nowych zmian:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

Aby znaleźć maksymalnie 50 plików o rozmiarze większym niż 10 KB:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Aby wykluczyć określony plik z indeksowania i dodać go do listy ignorowanych plików:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Aby wyświetlić wszystkie pliki, które nie są indeksowane:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Aby wyczyścić wcześniej indeksowane dane i ponownie uruchomić indeksowanie:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Aby zapisać całą historię zmian:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

Aby usunąć limit rozmiaru danych tymczasowych CodeLens i kontynuować indeksowanie niezależnie od tymczasowego rozmiaru danych:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Aby usunąć indeks kodu z potwierdzeniem:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Zarządzanie konfiguracją serwera za pomocą TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd)
