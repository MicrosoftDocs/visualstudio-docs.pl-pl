---
title: Generowanie kodu z języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37c60ed42e7d4a7604dc3d99f7e0311c7000b99c
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476511"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generowanie kodu z języka specyficznego dla domeny

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] oferują zaawansowane możliwości do generowania kodu, dokumenty, pliki konfiguracji i innych artefaktów z danych reprezentowanych w modelach. Za pomocą [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], można utworzyć zestaw klas, które reprezentują dane, można napisać szablony tekstowe w klasach których nazwy i właściwości odzwierciedlenia tych danych.

Na przykład firma Fabrikam ma plik XML nazw klienta i adresy e-mail. Ich deweloperom tworzenie modelu, w którym klient jest klasę o nazwie właściwości i wiadomości e-mail. Napisz ich kilka szablonów tekstu do przetwarzania danych, w tym ten fragment, który tworzy spis wszystkich klientów jako część strony HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Podczas przetwarzania bazy danych klientów w pliku XML jest do odczytu do magazynu modeli. A *procesora dyrektywy*utworzony za pomocą [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], udostępnia klasy klienta do kodu w szablonie tekstowym. Wiele szablonów tekstowych mogą być uruchamiane na tym samym magazynie.

Szablony tekstowe są istotne dla [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Są one używane do generowania kodu źródłowego dla elementów modelu domeny, a także pakietu VSPackage i kontrolek, które są używane do Zintegruj odpowiednie narzędzia, za pomocą programu Visual Studio.

W tej sekcji omówiono niektóre sposoby tworzenia, modyfikacji i szablony tekstowe używane w debugowania [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].

## <a name="in-this-section"></a>W tej sekcji

[Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu](../modeling/accessing-models-from-text-templates.md)\
Zawiera podstawowe informacje o odwoływaniu się do języka specyficznego dla domeny w szablonach tekstowych.

[Przewodnik: Debugowanie szablonu tekstowego uzyskującego dostęp do modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
W tym artykule opisano, jak to zrobić, rozwiązywanie problemów i debugowanie szablonu tekstu, który odwołuje się do języka specyficznego dla domeny.

[Przewodnik: Łączenie hosta z generowanym procesorem dyrektywy](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
W tym artykule opisano sposób łączenia niestandardowego hosta z generowanym procesorem dyrektywy.

[Dsltexttransform — polecenie](../modeling/the-dsltexttransform-command.md)\
W tym artykule opisano pliku polecenia, który jest wykonywany TextTransform plik wykonywalny w wierszu polecenia dla szablonów tekstowych, które odwołują się języki specyficzne dla domeny.

## <a name="reference"></a>Tematy pomocy

[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)\
Udostępnia składnia dyrektyw szablonu tekstu i bloki sterujące.

## <a name="related-sections"></a>Sekcje pokrewne

[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Wyjaśniono proces przekształcania szablonu tekstu.

[Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)\
Ten temat jest generowanie plików z DSL na serwerze kompilacji.