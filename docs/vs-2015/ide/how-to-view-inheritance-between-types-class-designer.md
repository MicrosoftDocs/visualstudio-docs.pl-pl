---
title: 'Instrukcje: wyświetlanie dziedziczenia między typami (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1e76d45847d0887b47746c60b836c7acf19d03b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670529"
---
# <a name="how-to-view-inheritance-between-types-class-designer"></a>Porady: wyświetlanie dziedziczenia pomiędzy typami (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Relację dziedziczenia można znaleźć, jeśli istnieje, między typem podstawowym a jego typami pochodnymi na diagramie klas w Projektant klas. Aby utworzyć relację dziedziczenia, jeśli nie istnieje, między dwoma typami, zobacz [How to: Create dziedziczenie między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-find-the-base-type"></a>Aby znaleźć typ podstawowy

1. Na diagramie klas kliknij typ, dla którego chcesz zobaczyć klasę bazową lub interfejs.

2. W menu **Diagram klas** wybierz **Pokaż klasę bazową** lub **Pokaż interfejsy podstawowe**.

    Na diagramie zostanie wybrana Klasa bazowa lub interfejs typu. Wszystkie ukryte linie dziedziczenia są teraz widoczne między dwoma kształtami.

   Możesz również kliknąć prawym przyciskiem myszy typ, którego typ podstawowy chcesz wyświetlić, a następnie wybierz polecenie **Pokaż klasę bazową** lub **Pokaż interfejsy podstawowe**.

### <a name="to-find-the-derived-types"></a>Aby znaleźć typy pochodne

1. Na diagramie klas kliknij typ, dla którego chcesz wyświetlić klasy pochodne lub interfejsy.

2. W menu **Diagram klas** wybierz pozycję **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

    Klasy pochodne lub interfejsy są wyświetlane na diagramie. Wszystkie ukryte linie dziedziczenia są teraz wyświetlane między kształtami.

   Możesz również kliknąć prawym przyciskiem myszy typ, dla którego chcesz zobaczyć typy pochodne, a następnie wybrać **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: tworzenie skojarzeń między typami (Projektant klas)](../ide/how-to-create-associations-between-types-class-designer.md) [Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)
