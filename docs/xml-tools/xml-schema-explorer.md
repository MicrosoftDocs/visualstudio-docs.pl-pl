---
title: Eksplorator schematu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07c5ba8d28a053b83481cf24e3bc1e450c28844e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050065"
---
# <a name="xml-schema-explorer"></a>Eksplorator schematu XML

**Eksploratora schematu XML** jest zintegrowana z usługą Microsoft Visual Studio i edytorem XML, aby umożliwić Praca ze schematami języka (XSD) definicji schematu XML. Po otwarciu pliku schematu XML **schemat ustawiony** węzeł jest dostępny w **Eksploratora schematu XML**. Wszystkich schematów uwzględniony, zaimportowanych lub zmieniony dla pliku docelowego, a także wszystkie pliki, które są wywoływane za pośrednictwem `include` lub `import` instrukcji, są również wyświetlane w **Eksploratora schematu XML**.

 **Eksploratora schematu XML** umożliwia wykonywanie następujących czynności:

- Uzyskaj krótkie omówienie zestawu schematu.

- Przeglądaj i przejdź drzewa.

- Wykonaj — słowo kluczowe i wyszukiwanie specyficzne dla schematu. Aby uzyskać więcej informacji, zobacz [wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md).

- Dodaj wyniki wyszukiwania do widoku wykresu i widoku modelu zawartości

- Sortuj drzewa w kolejności dokumentu, typ lub nazwa. Aby uzyskać więcej informacji, zobacz [sortowanie, filtrowanie i grupowanie](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Otwórz w edytorze XML, a następnie przejdź do lokalizacji kodu w pliku XSD. Aby uzyskać więcej informacji, zobacz [Integracja z edytorem XML](../xml-tools/integration-with-xml-editor.md).

- Wygeneruj przykładowy kod XML dla elementów globalnej.

**Eksploratora schematu XML** zapewnia hierarchiczna widok schematu ustawiana za pośrednictwem widoku drzewa. **Eksploratora schematu XML** także wyszukiwanie, filtrowanie, nawigacji i sortowania. Aby uzyskać dostęp do **Eksploratora schematu XML**, wykonaj jedną z następujących czynności:

- Jeśli użytkownik pracuje na [widoku Start](../xml-tools/start-view.md), kliknij przycisk **Eksploratora schematu XML** łącza.

- Jeśli użytkownik pracuje na [widoku wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) i mieć węzły w obszarze roboczym, użyj menu kontekstowe (kliknij prawym przyciskiem myszy), aby wybrać **Eksploratora schematu XML**.

- Możesz również wybrać **Eksploratora schematu XML** z **widoku** menu.

- Możesz uzyskać dostęp **Eksploratora schematu XML** z *.vb* pliku, który ma literał XML w Visual Basic, skojarzone z *XSD* pliku. Aby wyświetlić schemat zestaw w **Eksploratora schematu XML**, kliknij prawym przyciskiem myszy węzeł XML w literał XML lub importu przestrzeni nazw XML i wybierz **Pokaż w Eksploratorze schematu** polecenia. Aby uzyskać więcej informacji, zobacz [literały Integracja XML z Eksploratorem schematu XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Widok drzewa
 **Eksploratora schematu XML** schemat zawiera wstępnie skompilowany ustawić informacji w strukturze drzewa. Struktura drzewa jest zorganizowana w następujący sposób:

- Na najwyższym poziomie schematu ustawiono węzła.

- Drugi poziom zawiera przestrzenie nazw.

- Trzeci poziom zawiera pliki.

- Czwarty poziom zawiera globalny węzłów. Może to obejmować elementy, grupy, typów złożonych typów prostych, atrybuty, grup atrybutów i `include`, `import`, i `redefine` instrukcji.

Oto przykład struktury drzewa:

![Eksplorator schematu XML](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Wybór i aktywacja
 Aby zaznaczyć, a następnie wybierz węzeł, kliknij jeden raz w Eksploratorze schematu.

 Aby aktywować węzła, kliknij ją dwukrotnie lub naciśnij **Enter** po wybraniu węzła.

- Aktywowanie węzła spowoduje otwarcie pliku, w którym ten węzeł jest zdefiniowany (Jeśli plik nie jest już otwarty) i wybiera węzeł w pliku.

- Aktywowanie węzeł plików Otwiera wybrany plik (Jeśli nie jest już otwarty) i wyróżnienie `<schema>` węzła.

- Aktywowanie SchemaSet lub węzła obszaru nazw nic nie robi.

## <a name="drag-and-drop-nodes"></a>Przeciąganie i upuszczanie węzłów
 Możesz przeciągać i upuszczać globalnego węzłów, węzły plików i węzły przestrzeni nazw na widok Projektant XSD. Jeśli bieżący widok jest [widoku Start](../xml-tools/start-view.md), przeciągając węzeł do widoku spowoduje otwarcie [widoku wykresu](../xml-tools/graph-view.md). Jeśli bieżący widok jest [widoku modelu zawartości](../xml-tools/content-model-view.md) lub widoku wykresu widoku nie ulegnie zmianie, gdy upuścisz suszarkę węzła na niego.

 Upuszczanie plików w widoku doda wszystkie węzły globalne w pliku [obszaru roboczego Projektant XSD](../xml-tools/xml-schema-designer-workspace.md). Usunięcie przestrzeni nazw w widoku doda wszystkie węzły globalne w przestrzeni nazw do obszaru roboczego. Obszar roboczy jest współużytkowana przez wszystkie widoki.

 Nie można przeciągania i upuszczania węzłach lokalnym lub importów.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie węzłów do obszaru roboczego z Eksploratora schematu XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)