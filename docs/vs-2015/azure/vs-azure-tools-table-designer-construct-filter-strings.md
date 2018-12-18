---
title: Konstruowanie ciągi filtrów dla projektanta tabel | Dokumentacja firmy Microsoft
description: Konstruowanie ciągi filtrów dla projektanta tabel
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003584"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Konstruowanie ciągów filtrów dla projektanta tabel
## <a name="overview"></a>Omówienie
Aby filtrować dane w tabeli platformy Azure, która jest wyświetlana w programie Visual Studio **projektanta tabel**, utworzyć ciągu filtru i wprowadzić go w polu filtru. Składnia ciągu filtru jest definiowany przez usługi danych WCF i przypomina klauzulę WHERE języka SQL, ale są wysyłane do usługi tabeli za pomocą żądania HTTP. **Projektanta tabel** obsługuje poprawne kodowanie, więc aby odfiltrować wartość żądanej właściwości, należy podać tylko nazwę właściwości, operator porównania, wartości kryteriów i opcjonalnie, wartość logiczna operatora w polu filtru. Nie muszą zawierać opcję zapytania $filter, jak gdyby były konstruuje adres URL do wykonywania zapytań w tabeli za pomocą [dokumentacja interfejsu API REST usług Storage](http://go.microsoft.com/fwlink/p/?LinkId=400447).

Usługi danych WCF opierają się na [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Aby uzyskać szczegółowe informacje na temat opcję zapytania filtra systemu (**$filter**), zobacz [specyfikacji Konwencji identyfikatora URI OData](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Operatory porównania
Następujące operatory logiczne są obsługiwane dla wszystkich typów właściwości:

| Operator logiczny | Opis | Przykład ciągu filtru |
| --- | --- | --- |
| eq |Równa się |Miasto eq "Redmond" |
| gt |Większe niż |Cena gt 20 |
| GE |Większe niż lub równe |Cena ge 10 |
| lt |Mniejsze niż |Cena lt 20 |
| le |Mniejsze niż lub równe |Cena le 100 |
| ne |Nie równa się |Ne City "Londyn" |
| and |i |Cena le 200 i cena gt 3.5 |
| lub |Lub |Cena le 3.5 lub gt Cena 200 |
| not |nie |nie isAvailable |

Podczas tworzenia ciągu filtru, następujące reguły są ważne:

* Użyj operatorów logicznych, aby porównać właściwość z wartością. Należy pamiętać, że nie jest możliwe porównać właściwość z wartością dynamiczną; po jednej stronie wyrażenia musi być stałą.
* Wszystkie części ciągu filtru jest rozróżniana wielkość liter.
* Wartość stała muszą być tego samego typu danych co właściwość Aby filtr zwracał prawidłowe wyniki. Aby uzyskać więcej informacji na temat obsługiwanych typów właściwości, zobacz [opis modelu danych usługi Table Service](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Filtrowanie według właściwości ciągu
Podczas filtrowania właściwości ciągu stała typu string należy ją ująć w znaki pojedynczego cudzysłowu.

Poniższy przykład filtr **PartitionKey** i **RowKey** właściwości; dodatkowe niekluczowych również można dodawać właściwości ciągu filtru:

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Każde wyrażenie filtru można ująć w nawiasach, chociaż nie jest wymagane:

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Pamiętaj, że usługa Table service nie obsługuje symboli wieloznacznych zapytania nie są obsługiwane w Projektancie tabel albo. Można jednak wykonać Dopasowywanie przy użyciu operatorów porównania na żądaną prefiks prefiksów. Poniższy przykład zwraca jednostki z LastName właściwość rozpoczynająca się od litery "A":

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Filtrowanie według właściwości liczbowych
Aby filtrować liczbą całkowitą lub zmiennoprzecinkową, określ liczbę bez znaku cudzysłowu.

W tym przykładzie zwraca wszystkie jednostki z właściwością wiek, którego wartość jest większa niż 30:

    Age gt 30

W tym przykładzie zwraca wszystkie jednostki z właściwością AmountDue, którego wartość jest mniejsza niż lub równe 100.25:

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Filtrowanie według właściwości logiczne
Aby odfiltrować wartość logiczną, określ **true** lub **false** bez znaków cudzysłowu.

Poniższy przykład zwraca wszystkie jednostki, w których ustawiono właściwość IsActive **true**:

    IsActive eq true

Można także napisać to wyrażenie filtru, bez operatora logicznego. W poniższym przykładzie Usługa Table service zwróci wszystkich jednostek w przypadku IsActive **true**:

    IsActive

Aby zwrócić wszystkie jednostki, której IsActive ma wartość false, należy użyć not — operator:

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Filtrowanie według właściwości daty/godziny
Aby filtrować wartości daty/godziny, należy określić **daty/godziny** — słowo kluczowe, następuje Stała daty/godziny w znaki pojedynczego cudzysłowu. Stała daty/godziny musi być w formacie UTC połączone, zgodnie z opisem w [formatowanie wartości daty/godziny](http://go.microsoft.com/fwlink/p/?LinkId=400449).

Poniższy przykład zwraca jednostki, w którym właściwość CustomerSince jest równa 10 lipca 2008:

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
