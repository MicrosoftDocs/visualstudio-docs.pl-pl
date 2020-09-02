---
title: 'Instrukcje: pisanie wizualizatora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ce50276e4e83a1a055294c8e2b6e09cd0f93d54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833358"
---
# <a name="how-to-write-a-visualizer"></a>Porady: pisanie wizualizatora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać niestandardowy wizualizator dla obiektu dowolnej zarządzanej klasy z wyjątkiem dla <xref:System.Object> lub <xref:System.Array> .  
  
> [!NOTE]
> W aplikacjach ze **sklepu** obsługiwane są tylko Wizualizatory tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
 Architektura wizualizatora debugera ma dwie części:  
  
- *Strona debugera* działa w debugerze programu Visual Studio. Kod po stronie debugera tworzy i wyświetla interfejs użytkownika wizualizatora.  
  
- *Po stronie debugowanego obiektu* w procesie programu Visual Studio jest debugowane ( *debugowanego obiektu*).  
  
  Obiekt danych, który chcesz wizualizować (na przykład obiekt String) istnieje w procesie debugowanego obiektu. Dlatego po stronie debugowanego obiektu musi być wysyłany ten obiekt danych do strony debugera, która następnie może być wyświetlana przy użyciu utworzonego interfejsu użytkownika.  
  
  Po stronie debugera odbiera ten obiekt danych, który ma być wizualizacją od *dostawcy obiektów* , który implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfejs. Po stronie debugowanego obiektu wysyła obiekt danych za pośrednictwem *źródła obiektu*, który pochodzi od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Dostawca obiektów może również wysyłać dane z powrotem do źródła obiektów, co pozwala napisać wizualizator, który edytuje, a także wyświetla dane. Dostawcę obiektów można zastąpić, aby komunikować się z ewaluatora wyrażeń i w związku z tym ze źródłem obiektów  
  
  Po stronie debugowanego obiektu i debuger komunikują się ze sobą za pomocą <xref:System.IO.Stream> . Podano metody serializacji obiektu danych do <xref:System.IO.Stream> i deserializacji z <xref:System.IO.Stream> powrotem do obiektu danych.  
  
  Kod po stronie debugowanego obiektu jest określany przy użyciu atrybutu DebuggerVisualizer ( <xref:System.Diagnostics.DebuggerVisualizerAttribute> ).  
  
  Aby utworzyć interfejs użytkownika wizualizatora po stronie debugera, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> i zastąpić <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę, aby wyświetlić interfejs.  
  
  Możesz użyć <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> , aby wyświetlić formularze systemu Windows, okna dialogowe i kontrolki ze wizualizatora.  
  
  Obsługa typów ogólnych jest ograniczona. Można napisać wizualizator dla elementu docelowego, który jest typem ogólnym tylko wtedy, gdy typ ogólny jest typem otwartym. To ograniczenie jest takie samo jak w przypadku ograniczenia przy użyciu `DebuggerTypeProxy` atrybutu. Aby uzyskać szczegółowe informacje, zobacz [Używanie atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Wizualizacje niestandardowe mogą mieć uwagi dotyczące zabezpieczeń. Zobacz [zagadnienia dotyczące zabezpieczeń wizualizatora](../debugger/visualizer-security-considerations.md).  
  
  Poniższe procedury zapewniają ogólny widok, co należy zrobić, aby utworzyć wizualizator. Aby uzyskać bardziej szczegółowy opis, zobacz [Przewodnik: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Aby utworzyć stronę debugera  
  
1. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metod, aby uzyskać wizualizację obiektu po stronie debugera.  
  
2. Utwórz klasę, która dziedziczy z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> .  
  
3. Zastąp <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę, aby wyświetlić interfejs. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metod do wyświetlania formularzy, okien dialogowych i kontrolek systemu Windows w ramach interfejsu.  
  
4. Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute> , dając mu wizualizator ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).  
  
### <a name="to-create-the-debuggee-side"></a>Aby utworzyć stronę debugowanego obiektu  
  
1. Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute> , dając mu wizualizator ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ) i źródło obiektu ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). W przypadku pominięcia źródła obiektów zostanie użyte domyślne źródło obiektu.  
  
2. Jeśli chcesz, aby wizualizator mógł edytować obiekty danych, a także je wyświetlić, musisz zastąpić `TransferData` `CreateReplacementObject` metody lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md)   
 [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Instrukcje: testowanie i debugowanie wizualizatora](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Zagadnienia dotyczące zabezpieczeń internetowych](../debugger/visualizer-security-considerations.md)
