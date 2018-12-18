---
title: 'Porady: pisanie wizualizatora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c7f1fa96bba40e5e56ca7f054b683b3243de65b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724895"
---
# <a name="how-to-write-a-visualizer"></a>Porady: pisanie wizualizatora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz napisać niestandardowego wizualizatora obiektu klasy zarządzanej z wyjątkiem <xref:System.Object> lub <xref:System.Array>.  
  
> [!NOTE]
>  W **Store** aplikacji, tylko standardowy tekst, HTML, XML i JSON wizualizatory są obsługiwane. Wizualizatory niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
 Architektura wizualizatora debuger ma dwie części:  
  
- *Debugera po stronie* jest uruchamiany w ramach debugera programu Visual Studio. Kod po stronie debugera tworzy i wyświetla interfejsu użytkownika dla usługi wizualizatora.  
  
- *Po stronie debugowanego obiektu* jest uruchamiany w ramach procesu programu Visual Studio debuguje ( *obiekt debugowany*).  
  
  Obiekt danych, które mają być wyświetlane (na przykład obiekt ciągu) istnieje w obiekcie debugowanym procesie. Dlatego po stronie debugowanego obiektu ma wysyłać ten obiekt danych po stronie debugera, który można następnie wyświetlać je za pomocą interfejsu użytkownika, które można utworzyć.  
  
  Po stronie debugera otrzyma ten obiekt danych, aby być wizualizowane z *dostawcy obiektów* implementującej <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfejsu. Po stronie debugowanego obiektu wysyła obiekt danych za pośrednictwem *źródła obiektu*, który pochodzi od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Dostawcy obiektów można również wysyłać dane z powrotem do źródła obiektu, który umożliwia pisanie wizualizatora, który umożliwia edycję, a także wyświetla dane. Dostawcy obiektów może zostać zastąpiona w celu komunikować Ewaluator wyrażeń i dlatego źródła obiektu  
  
  Po stronie debugowanego obiektu i debuger komunikować się ze sobą za pośrednictwem <xref:System.IO.Stream>. Metody są dostarczane do serializacji obiektu danych do <xref:System.IO.Stream> i deserializacji <xref:System.IO.Stream> do obiektu danych.  
  
  Kod po stronie debugowanego obiektu jest określony za pomocą atrybutu DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
  Do tworzenia interfejsu użytkownika wizualizatora po stronie debugera, należy utworzyć klasę, która dziedziczy po elemencie <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> i zastąpić <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu.  
  
  Możesz użyć <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> do wyświetlania formularzy Windows, okien dialogowych i formantów z Twojej wizualizatora.  
  
  Obsługa typów ogólnych jest ograniczona. Można napisać Wizualizator dla obiektu docelowego, który jest typem ogólnym, tylko wtedy, gdy typ ogólny jest typem otwartym. To ograniczenie jest taka sama jak wartość ograniczenia, korzystając z `DebuggerTypeProxy` atrybutu. Aby uzyskać więcej informacji, zobacz [przy użyciu atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Wizualizatory niestandardowe mogą mieć zagadnienia związane z zabezpieczeniami. Zobacz [zagadnienia dotyczące zabezpieczeń internetowych](../debugger/visualizer-security-considerations.md).  
  
  Procedury opisane poniżej, zapewniają ogólny widok co należy zrobić, aby utworzyć wizualizatora. Aby uzyskać bardziej szczegółowy opis, zobacz [wskazówki: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Aby utworzyć po stronie debugera  
  
1.  Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metody w celu uzyskania wizualizowanego obiektu po stronie debugera.  
  
2.  Utwórz klasę, która dziedziczy z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Zastąp <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metody w celu wyświetlenia formularzy Windows, okien dialogowych i formantów w ramach interfejsu.  
  
4.  Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute>, nadając mu wizualizatora (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Aby utworzyć po stronie debugowanego obiektu  
  
1.  Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute>, nadając mu wizualizatora (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) i źródła obiektu (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Jeżeli pominięto źródła obiektu, będą używane domyślne źródło obiektu  
  
2.  Jeśli chcesz, aby Twoje visualizer, aby można było edytować obiekty danych, również zgodnie z ich, wyświetlić należy zastąpić `TransferData` lub `CreateReplacementObject` metody z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)   
 [Porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Porady: testowanie i debugowanie Wizualizera](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Zagadnienia dotyczące zabezpieczeń wizualizatora](../debugger/visualizer-security-considerations.md)



