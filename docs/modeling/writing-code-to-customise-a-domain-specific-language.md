---
title: Dostosowywanie języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b67a50623eb1924c4a18b57524c409f7eba6ab20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546877"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny

W tej sekcji pokazano, jak używać niestandardowego kodu do uzyskiwania dostępu do modelu w języku specyficznym dla domeny, modyfikowania go lub tworzenia.

Istnieje kilka kontekstów, w których można napisać kod, który działa z DSL:

- **Polecenia niestandardowe.** Można utworzyć polecenie, które użytkownicy mogą wywołać, klikając prawym przyciskiem myszy diagram, a następnie modyfikując model. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Zatwierdzenia.** Można napisać kod, który weryfikuje, czy model jest w poprawnym stanie. Aby uzyskać więcej informacji, zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md).

- **Zastępowanie zachowania domyślnego.** Można modyfikować wiele aspektów kodu, który jest generowany z DslDefinition. DSL. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).

- **Przekształcanie tekstu.** Można napisać szablony tekstowe, które zawierają kod, który uzyskuje dostęp do modelu i generuje plik tekstowy, na przykład w celu wygenerowania kodu programu. Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

- **Inne rozszerzenia programu Visual Studio.** Można napisać oddzielne rozszerzenia VSIX, które odczytują i modyfikują modele. Aby uzyskać więcej informacji, zobacz [jak to zrobić: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Wystąpienia klas, które definiujesz w DslDefinition. DSL, są przechowywane w strukturze danych o nazwie *Magazyn w pamięci* (IMS) lub w *sklepie*. Klasy zdefiniowane w DSL zawsze przyjmują magazyn jako argument do konstruktora. Na przykład, jeśli DSL definiuje klasę o nazwie example:

`Example element = new Example (theStore);`

przechowywanie obiektów w sklepie (zamiast zwykłych obiektów) zapewnia kilka korzyści.

- **Transakcje**. Można grupować serie powiązanych zmian w transakcji:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Jeśli wystąpi wyjątek w czasie wprowadzania zmian, w związku z czym końcowe zatwierdzenie () nie zostanie wykonane, magazyn zostanie zresetowany do poprzedniego stanu. Dzięki temu można upewnić się, że błędy nie opuszczają modelu w stanie niespójnym. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Relacje binarne**. Jeśli zdefiniujesz relację między dwoma klasami, wystąpienia na obu końcach mają właściwość, która przechodzi do drugiego końca. Dwa zakończenia są zawsze zsynchronizowane. Na przykład w przypadku zdefiniowania relacji Parenthood z rolami o nazwie rodzice i Children można napisać:

     `John.Children.Add(Mary)`

     Oba poniższe wyrażenia są teraz prawdziwe:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Możesz również osiągnąć ten sam efekt, pisząc:

     `Mary.Parents.Add(John)`

     Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Zasady i zdarzenia**. Można zdefiniować reguły wyzwalane po wprowadzeniu określonych zmian. Reguły są używane na przykład w celu zachowania aktualności kształtów na diagramie przy użyciu elementów modelu, które są obecne. Aby uzyskać więcej informacji, zobacz [reagowanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

- **Serializacja**. Magazyn zapewnia standardowy sposób serializacji obiektów, które zawiera do pliku. Można dostosować reguły serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie serializacji File Storage i XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)