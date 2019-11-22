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
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293404"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Porady: odpowiadanie na zmiany w modelu UML
Można napisać kod, który jest wykonywany po każdym wystąpieniu zmiany w modelu UML w programie Visual Studio. Będzie ona reagować na zmiany wprowadzane bezpośrednio przez użytkownika i inne rozszerzenia programu Visual Studio. Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Te techniki nie są obsługiwane przez interfejs API UML. Mogą one nie zadziałały w przyszłych wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 [Nawigowanie po programie obsługi zdarzeń modelu UML](../modeling/navigate-the-uml-model.md) [propagowanie zmian poza model](../modeling/event-handlers-propagate-changes-outside-the-model.md) [próbki: kolor według stereotypu](https://go.microsoft.com/fwlink/?LinkId=213841)