---
title: 'Instrukcje: reagowanie na zmiany w modelu UML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf88661f9ec15e1a3a25e7eb6a40bbd82335a7f4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918723"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Porady: odpowiadanie na zmiany w modelu UML
Można napisać kod, który jest wykonywany po każdym wystąpieniu zmiany w modelu UML w programie Visual Studio. Będzie ona reagować na zmiany wprowadzane bezpośrednio przez użytkownika i inne rozszerzenia programu Visual Studio. Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Te techniki nie są obsługiwane przez interfejs API UML. Mogą one nie zadziałały w przyszłych wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 Przechodzenie obsługi zdarzeń [modelu UML](../modeling/navigate-the-uml-model.md) [propaguje zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)
 