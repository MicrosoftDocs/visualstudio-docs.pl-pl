---
title: Dostosowywanie języka specyficznego dla domeny
description: Dowiedz się, jak używać kodu niestandardowego do uzyskiwania dostępu do modelu, modyfikowania go lub tworzenia go w języku specyficznym dla domeny (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2231ef94bee01558e2c26899a5d9a0c855489e94
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388051"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny

W tej sekcji pokazano, jak używać kodu niestandardowego do uzyskiwania dostępu do modelu, modyfikowania go lub tworzenia go w języku specyficznym dla domeny.

Istnieje kilka kontekstów, w których można napisać kod, który działa z DSL:

- **Polecenia niestandardowe.** Możesz utworzyć polecenie, które użytkownicy mogą wywołać, klikając prawym przyciskiem myszy diagram i modyfikując model. Aby uzyskać więcej informacji, zobacz How to: Add a Command to the Shortcut Menu (Jak dodać polecenie [do menu skrótów).](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

- **Sprawdzania poprawności.** Możesz napisać kod, który weryfikuje, czy model jest w poprawnym stanie. Aby uzyskać więcej informacji, zobacz [Validation in a Domain-Specific Language (Walidacja w Domain-Specific języku](../modeling/validation-in-a-domain-specific-language.md)).

- **Zastępowanie domyślnego zachowania.** Można zmodyfikować wiele aspektów kodu, który jest generowany z DslDefinition.dsl. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).

- **Przekształcanie tekstu.** Można pisać szablony tekstowe zawierające kod, który uzyskuje dostęp do modelu i generuje plik tekstowy, na przykład w celu wygenerowania kodu programu. Aby uzyskać więcej informacji, zobacz [Generowanie kodu z Domain-Specific języku](../modeling/generating-code-from-a-domain-specific-language.md).

- **Inne Visual Studio rozszerzenia.** Można pisać oddzielne rozszerzenia VSIX, które odczytuje i modyfikuje modele. Aby uzyskać więcej informacji, [zobacz How to: Open a Model from File in Program Code](../modeling/how-to-open-a-model-from-file-in-program-code.md) (Jak otworzyć model z pliku w kodzie programu)

Wystąpienia klas, które definiujesz w DslDefinition.dsl, są przechowywane  w strukturze danych nazywanej magazynem w pamięci (IMS) lub *magazynem*. Klasy, które definiujesz w DSL zawsze mają store jako argument do konstruktora. Jeśli na przykład DSL definiuje klasę o nazwie Przykład:

`Example element = new Example (theStore);`

Przechowywanie obiektów w magazynie (zamiast zwykłych obiektów) zapewnia kilka korzyści.

- **Transakcje**. Możesz zgrupować serię powiązanych zmian w transakcję:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Jeśli podczas zmian wystąpi wyjątek, tak aby ostateczne zatwierdzenie () nie było wykonywane, magazyn zostanie zresetowany do poprzedniego stanu. Pomaga to upewnić się, że błędy nie pozostawiają modelu w niespójnym stanie. Aby uzyskać więcej informacji, zobacz [Nawigowanie po](../modeling/navigating-and-updating-a-model-in-program-code.md)modelu i aktualizowanie go w kodzie programu .

- **Relacje binarne**. Jeśli zdefiniujesz relację między dwiema klasami, wystąpienia na obu końcach mają właściwość, która przechodzi do drugiego końca. Oba zakończenia są zawsze zsynchronizowane. Jeśli na przykład zdefiniujesz relację nawiasów z rolami o nazwach Nadrzędny i Podrzędny, możesz napisać:

     `John.Children.Add(Mary)`

     Oba następujące wyrażenia są teraz prawdziwe:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Ten sam efekt można również osiągnąć, pisząc:

     `Mary.Parents.Add(John)`

     Aby uzyskać więcej informacji, zobacz [Nawigowanie po](../modeling/navigating-and-updating-a-model-in-program-code.md)modelu i aktualizowanie go w kodzie programu .

- **Reguły i zdarzenia**. Można zdefiniować reguły, które są wyzłoszone po każdym wymusiniu określonych zmian. Reguły są używane na przykład w celu zachowania na bieżąco kształtów na diagramie z elementami modelu, które są przez nie obecne. Aby uzyskać więcej informacji, zobacz [Odpowiadanie na zmiany i propagowanie ich.](../modeling/responding-to-and-propagating-changes.md)

- **Serializacja**. Magazyn zapewnia standardowy sposób serializacji obiektów, które zawiera do pliku. Można dostosować reguły serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)