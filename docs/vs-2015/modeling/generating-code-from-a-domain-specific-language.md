---
title: Generowanie kodu z języka specyficznego dla domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666111"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generowanie kodu z języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Firma Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] zapewnia zaawansowany sposób generowania kodu, dokumentów, plików konfiguracji i innych artefaktów z danych przedstawionych w modelach. Za pomocą programu [!INCLUDE[dsl](../includes/dsl-md.md)] można utworzyć zestaw klas, które reprezentują dane, i można napisać szablony tekstowe w klasach, których nazwy i właściwości odzwierciedlają te dane.

 Na przykład firma Fabrikam ma plik XML z nazwami klientów i adresami e-mail. Deweloperzy tworzą model, w którym klient jest klasą z właściwościami nazwa i adres e-mail. Piszą one kilka szablonów tekstowych do przetwarzania danych, w tym ten fragment, który tworzy tabelę wszystkich klientów w ramach strony HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Podczas przetwarzania bazy danych klienta plik XML jest odczytywany do magazynu modeli. *Procesor dyrektywy*utworzony przy użyciu [!INCLUDE[dsl](../includes/dsl-md.md)] , sprawia, że Klasa klienta jest dostępna dla kodu w szablonie tekstu. Wiele szablonów tekstowych można uruchamiać w ramach tego samego magazynu.

 Szablony tekstowe mają kluczowe znaczenie [!INCLUDE[dsl](../includes/dsl-md.md)] . Są one używane do generowania kodu źródłowego dla elementów modelu domeny oraz dla pakietu VSPackage i formantów, które są używane do integracji narzędzi z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 W tej sekcji omówiono niektóre sposoby tworzenia, modyfikowania i debugowania szablonów tekstu używanych w programie [!INCLUDE[dsl](../includes/dsl-md.md)] .

## <a name="in-this-section"></a>W tej sekcji
 [Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu](../modeling/accessing-models-from-text-templates.md)

 Zawiera podstawowe informacje dotyczące odwoływania się do języka specyficznego dla domeny w szablonach tekstowych.

 [Przewodnik: Debugowanie szablonu tekstowego uzyskującego dostęp do modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Opisuje sposób rozwiązywania problemów i debugowania dla szablonu tekstu, który odwołuje się do języka specyficznego dla domeny.

 [Wskazówki: łączenie hosta z generowanym procesorem dyrektywy](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Opisuje sposób nawiązywania połączenia z hostem niestandardowym z wygenerowanym procesorem dyrektywy.

 [DslTextTransform — Polecenie](../modeling/the-dsltexttransform-command.md)

 Opisuje plik poleceń, który wykonuje element wykonywalny TextTransform w wierszu polecenia dla szablonów tekstowych, które odwołują się do języków specyficznych dla domeny.

## <a name="reference"></a>Dokumentacja
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)

 Zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.

## <a name="related-sections"></a>Sekcje pokrewne
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Wyjaśnia proces transformacji szablonu tekstu.

 [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)

 Zapoznaj się z tym tematem, Jeśli generujesz pliki z DSL na serwerze kompilacji.
