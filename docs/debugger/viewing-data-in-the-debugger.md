---
title: Tworzenie niestandardowych widoków danych w debugerze | Microsoft Docs
description: Poznaj różne sposoby sprawdzania i modyfikowania stanu programu w debugerze programu Visual Studio. Obejmują one funkcje autouzupełniania i oglądania, podpowiedzi i wizualizatorów.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5acac83a6d461f6b7301ff2bfe89d92dc78d00ee
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149914"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Tworzenie niestandardowych widoków danych w debugerze programu Visual Studio (C#, Visual Basic, C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Debuger udostępnia wiele narzędzi do sprawdzania i modyfikowania stanu programu. Większość z tych narzędzi działa tylko w trybie przerwania.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Tworzenie niestandardowych widoków danych w oknach zmiennych i na etykietkach

 Wiele [okien debugera](../debugger/debugger-windows.md), takich jak okna **autouzupełniania** i **czujki** , umożliwiają inspekcję zmiennych. Możesz dostosować sposób, w jaki typy C++, obiekty zarządzane i własne typy są wyświetlane w oknach zmiennych debugera i w [etykietkach](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)danych. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych widoków obiektów C++](../debugger/create-custom-views-of-native-objects.md) i [Tworzenie widoków niestandardowych obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Tworzenie wizualizacji niestandardowych

 Wizualizatory umożliwiają wyświetlanie zawartości obiektu lub zmiennej w zrozumiały sposób. W debugerze programu Visual Studio, wizualizator odwołuje się do różnych okien, które można otworzyć za pomocą ikony lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora") . Na przykład wizualizator HTML pokazuje, jak ciąg HTML będzie interpretowany i wyświetlany w przeglądarce. Można uzyskać dostęp do wizualizatorów ze wskazówek dotyczących danych, okna **czujki** , okna **Autostart** i okna **zmiennych lokalnych** . Okno dialogowe **QuickWatch** zawiera również wizualizator. Aby uzyskać więcej informacji, zobacz [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Zobacz także

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Okno polecenia](../ide/reference/command-window.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
