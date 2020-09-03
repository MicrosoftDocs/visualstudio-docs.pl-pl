---
title: Dokumentacja interfejsu API dla rozszerzalności modelowania UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672806"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Wykaz interfejsów API dla rozszerzalności modelowania UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod programu, aby odczytywać i modyfikować modele tworzone w programie Visual Studio. Dokumentacja interfejsu API zawiera informacje o określonych klasach, które ułatwiają to. Aby uzyskać więcej informacji zorientowanych na zadania, zapoznaj się z tematami w sekcji [rozszerzając modele UML i diagramy](../modeling/extend-uml-models-and-diagrams.md). Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Zestawy

|Zestaw|Co można zrobić|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|— Odczytywanie i zmiana elementów modelu, takich jak IUseCase, IAssociation i tak dalej.<br />-Nawigowanie między elementami.<br /><br /> Przestrzenie nazw i typy odpowiadają tym, które są zdefiniowane w specyfikacji UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Utwórz nowe wystąpienia elementów modelu<br />— Dostęp i modyfikowanie kształtów i diagramów.|

## <a name="see-also"></a>Zobacz też
 [Rozszerzona dokumentacja modelu UML i diagramy](../modeling/extend-uml-models-and-diagrams.md) [interfejsów API dla zestawu SDK modelowania dla programu Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
