---
title: Konstruowanie ciągów filtru dla projektanta tabel | Microsoft Docs
description: Konstruowanie ciągów filtru dla projektanta tabel
author: ghogen
manager: jillfra
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 571f7bf825583b3094e07ea4404437f2fb2d62de
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917603"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Konstruowanie ciągów filtrów dla projektanta tabel
## <a name="overview"></a>Omówienie
Aby filtrować dane w tabeli platformy Azure, która jest wyświetlana w **Projektancie tabel**programu Visual Studio, należy utworzyć ciąg filtru i wprowadzić go w polu filtru. Składnia ciągu filtru jest definiowana przez Usługi danych programu WCF i jest podobna do klauzuli SQL WHERE, ale jest wysyłana do Table service za pośrednictwem żądania HTTP. **Projektant tabel** obsługuje odpowiednie kodowanie, dlatego w celu filtrowania według żądanej wartości właściwości należy wprowadzić tylko nazwę właściwości, operator porównania, wartość kryteriów i opcjonalnie operator logiczny w polu filtru. Nie trzeba dołączać opcji zapytania $filter tak samo, jak w przypadku konstruowania adresu URL w celu zbadania tabeli za pośrednictwem [dokumentacji interfejsu API REST usług Storage](/rest/api/storageservices).

Usługi danych programu WCF opierają się na [protokole Open Data Protocol](https://www.odata.org/) (OData). Aby uzyskać szczegółowe informacje na temat opcji filtrowania systemu kwerend ( **$Filter**), zobacz [specyfikację identyfikatorów URI usługi OData](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

## <a name="comparison-operators"></a>Operatory porównania
Następujące operatory logiczne są obsługiwane dla wszystkich typów właściwości:

| Operator logiczny | Opis | Przykładowy ciąg filtru |
| --- | --- | --- |
| eq |Równa się |Miasto EQ "Redmond" |
| gt |Większe niż |Cena gt 20 |
| stron |Większe niż lub równe |Cena GE 10 |
| lt |Mniejsze niż |Cena lt 20 |
| urządzeń |Mniejsze niż lub równe |Cena Le 100 |
| ne |Nie równa się |Miasto (Londyn) |
| and |Oraz |Cena Le 200 i cena gt 3,5 |
| lub |Lub |Cena Le 3,5 lub cena gt 200 |
| not |nie |nie IsAvailable |

Podczas konstruowania ciągu filtru ważne są następujące reguły:

* Operatory logiczne służą do porównywania właściwości z wartością. Należy pamiętać, że nie można porównać właściwości z wartością dynamiczną; jedna ze stron wyrażenia musi być stałą.
* We wszystkich częściach ciągu filtru jest rozróżniana wielkość liter.
* Wartość stała musi mieć ten sam typ danych co właściwość, aby filtr zwracał prawidłowe wyniki. Aby uzyskać szczegółowe informacje na temat obsługiwanych typów właściwości, zobacz [Omówienie modelu danych usługi Table service](/rest/api/storageservices/Understanding-the-Table-Service-Data-Model).

## <a name="filtering-on-string-properties"></a>Filtrowanie właściwości ciągu
W przypadku filtrowania według właściwości ciągu ujmij ciąg w znaki pojedynczego cudzysłowu.

Poniższe przykładowe filtry we właściwościach **PartitionKey** i **RowKey** ; do ciągu filtru można również dodać dodatkowe właściwości niebędące kluczami:

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

Każde wyrażenie filtru można ująć w nawiasy, chociaż nie jest to wymagane:

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

Należy zauważyć, że Table service nie obsługuje zapytań wieloznacznych i nie są obsługiwane w Projektancie tabel. Można jednak wykonać dopasowanie prefiksu przy użyciu operatorów porównania na żądanym prefiksie. Poniższy przykład zwraca jednostki z właściwością LastName rozpoczynającą się literą "A":

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>Filtrowanie na właściwościach liczbowych
Aby odfiltrować liczbę całkowitą lub zmiennoprzecinkową, określ liczbę bez znaków cudzysłowu.

Ten przykład zwraca wszystkie jednostki z właściwością wieku, której wartość jest większa niż 30:

```
Age gt 30
```

Ten przykład zwraca wszystkie jednostki z właściwością AmountDue, której wartość jest mniejsza lub równa 100,25:

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>Filtrowanie właściwości logicznych
Aby odfiltrować wartość logiczną, należy określić **wartość PRAWDA** lub **Fałsz** bez znaków cudzysłowu.

Poniższy przykład zwraca wszystkie jednostki, w których właściwość IsActive jest ustawiona na **wartość true**:

```
IsActive eq true
```

Możesz również napisać wyrażenie filtru bez operatora logicznego. W poniższym przykładzie Table service zwróci również wszystkie jednostki, gdzie IsActive jest **prawdziwe**:

```
IsActive
```

Aby zwrócić wszystkie jednostki, w których IsActive ma wartość false, można użyć operatora not:

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>Filtrowanie właściwości DateTime
Aby odfiltrować wartość daty i godziny, określ słowo kluczowe **DateTime** , po którym następuje stała Data/godzina w pojedynczym cudzysłowie. Stała Data/godzina musi być w formacie połączonym UTC, zgodnie z opisem w temacie [Formatowanie wartości właściwości DateTime](/rest/api/storageservices/Formatting-DateTime-Property-Values).

Poniższy przykład zwraca jednostki, w których właściwość CustomerSince jest równa 10 lipca 2008:

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```
