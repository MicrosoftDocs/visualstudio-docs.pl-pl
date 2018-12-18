---
title: Weryfikacja systemu w czasie projektowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 03cac924853f4348faabd773260a9512c2d82b6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760971"
---
# <a name="validate-your-system-during-development"></a>Weryfikacja systemu w czasie opracowywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio może pomóc zachować oprogramowania zgodne z wymagań użytkowników oraz przy użyciu architektury Twojego systemu.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdą z tych funkcji, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Kluczowe zadania  
 Aby zweryfikować swoje oprogramowanie, należy wykonać poniższe zadania.  
  
|**Zadania**|**Skojarzone tematy**|  
|---------------|---------------------------|  
|**Sprawdź, czy model jest spójna:**<br /><br /> Zależnie od sposobu projekt używa i interpretuje modeli może być przydatne do odrzucenia niektóre kombinacje elementów. Na przykład można ograniczyć klas UML, aby zawsze mieć [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]— nazwy zgodne. Można zdefiniować ograniczenia, takie jak te w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia.|-   [Weryfikacja modelu UML](../modeling/validate-your-uml-model.md)<br />-   [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)|  
|**Upewnij się, oprogramowaniu spełnia wymagania użytkowników**:<br /><br /> Wymagania i modele architektury można użyć, aby ułatwić organizowanie testów systemu i jego składników. Praktyka ta pomaga zagwarantować, że testowania wymagań które są ważne dla użytkowników i innych zainteresowanych stron i pomaga szybko aktualizować testów, gdy zmienią się wymagania.|-   [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)|  
|**Upewnij się, że oprogramowanie pozostanie spójna z zamierzonego projektu systemu:**<br /><br /> Diagramy warstwowe opisywanie zakładanych zależności między składnikami aplikacji. Podczas tworzenia aplikacji można sprawdzić, że rzeczywiste zależności w kodzie są zgodne z zamierzonego projektu.|-   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Filmy wideo**|![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [witryny Channel 9: Doug siedem: rozpoznawanie kodu oraz projekt systemu w programie Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [witryny Channel 9: Projektowanie aplikacji przy użyciu diagramu warstwowego](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") [serii MSDN jak mogę: jak sprawdzić poprawność kodu przy użyciu diagramów warstw](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogi**|-   [Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Artykuły techniczne i dzienniki**|[Centrum MSDN architektury](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)



