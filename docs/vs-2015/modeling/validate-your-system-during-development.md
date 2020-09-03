---
title: Weryfikuj system podczas programowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1beeef572282a642e4a989086ac0fd228409fec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586267"
---
# <a name="validate-your-system-during-development"></a>Weryfikacja systemu w czasie opracowywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio może pomóc zapewnić zgodność oprogramowania z wymaganiami użytkowników i architekturą systemu.

 Aby sprawdzić, które wersje programu Visual Studio obsługują każdą z tych funkcji, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Najważniejsze zadania
 Aby sprawdzić poprawność oprogramowania, należy wykonać poniższe zadania.

|**Zadania**|**Skojarzone tematy**|
|---------------|---------------------------|
|**Upewnij się, że model jest spójny:**<br /><br /> W zależności od sposobu, w jaki projekt używa i interpretuje modele, może być przydatne, aby nie zezwalać na niektóre kombinacje elementów. Można na przykład ograniczyć klasy UML, aby zawsze miały one [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] zgodne nazwy. Można definiować ograniczenia takie jak te w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeniach.|-   [Weryfikowanie modelu UML](../modeling/validate-your-uml-model.md)<br />-   [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)|
|Upewnij **się, że oprogramowanie spełnia wymagania użytkowników**:<br /><br /> Aby ułatwić organizowanie testów systemu i jego składników, można użyć wymagań i modeli architektonicznych. Dzięki temu można sprawdzić wymagania, które są ważne dla użytkowników i innych uczestników projektu, oraz ułatwić szybkie aktualizowanie testów w przypadku zmiany wymagań.|-   [Opracowywanie testów z modelu](../modeling/develop-tests-from-a-model.md)|
|**Upewnij się, że oprogramowanie pozostaje spójne z zamierzonym projektem systemu:**<br /><br /> Diagramy warstw opisują zamierzone zależności między składnikami aplikacji. Podczas opracowywania można sprawdzić, czy rzeczywiste zależności w kodzie są zgodne z zamierzonym projektem.|-   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Sprawdzanie poprawności kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|------------------|---------------|
|**Filmy wideo**|![link do kanału wideo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug siedem: zrozumienie kodu i projekt systemu przy użyciu programu Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link do kanału wideo](../data-tools/media/playvideo.gif "PlayVideo") [9: projektowanie aplikacji przy użyciu diagramu warstwowego](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN: jak to zrobić, w jaki sposób można sprawdzić poprawność kodu przy użyciu diagramów warstw](https://msdn.microsoft.com/vstudio/gg501755)|
|**Fora**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Wizualizacja & modelowania SDK (narzędzia DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogi**|-   [Blog programu Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Artykuły techniczne i dzienniki**|[Centrum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Zobacz też
 [Testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [rozszerzając modele UML i diagramy](../modeling/extend-uml-models-and-diagrams.md) [model wymagania użytkownika](../modeling/model-user-requirements.md) [analizowanie i architektura modelowania](../modeling/analyze-and-model-your-architecture.md)
