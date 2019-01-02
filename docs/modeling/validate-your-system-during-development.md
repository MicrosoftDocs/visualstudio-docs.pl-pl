---
title: Weryfikacja systemu w czasie opracowywania
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0878291441f6fe5d5237c0317b3df631aefee139
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869323"
---
# <a name="validate-your-system-during-development"></a>Weryfikacja systemu w czasie opracowywania
Visual Studio może pomóc zachować oprogramowania zgodne z wymagań użytkowników oraz przy użyciu architektury Twojego systemu.

 Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdą z tych funkcji, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Kluczowe zadania
 Aby zweryfikować swoje oprogramowanie, należy wykonać poniższe zadania.

|**Zadania**|**Skojarzone tematy**|
|-|-|
|**Upewnij się, oprogramowaniu spełnia wymagania użytkowników**:<br /><br /> Wymagania i modele architektury można użyć, aby ułatwić organizowanie testów systemu i jego składników. Praktyka ta pomaga zagwarantować, że testowania wymagań które są ważne dla użytkowników i innych zainteresowanych stron i pomaga szybko aktualizować testów, gdy zmienią się wymagania.|-   [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)|
|**Upewnij się, że oprogramowanie pozostanie spójna z zamierzonego projektu systemu:**<br /><br /> Diagramy zależności opisywanie zakładanych zależności między składnikami aplikacji. Podczas tworzenia aplikacji można sprawdzić, że rzeczywiste zależności w kodzie są zgodne z zamierzonego projektu.|-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Łącza**|
|-|-|
|**Filmy wideo**|![Link do klipu wideo](../data-tools/media/playvideo.gif) [witryny Channel 9: Doug 7: Rozpoznawanie kodu oraz projekt systemu w programie Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![Link do klipu wideo](../data-tools/media/playvideo.gif) [witryny Channel 9: Projektowanie aplikacji przy użyciu diagramów zależności](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![Link do klipu wideo](../data-tools/media/playvideo.gif) [MSDN jak mogę serii: Jak sprawdzić poprawność kodu przy użyciu diagramów zależności](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogi**|-   [Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)|
|**Artykuły techniczne i dzienniki**|[Centrum MSDN architektury](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Zobacz także

- [Testowanie aplikacji](/azure/devops/test/overview?view=vsts)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
