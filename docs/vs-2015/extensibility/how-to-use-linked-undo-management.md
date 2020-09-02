---
title: 'Instrukcje: korzystanie z połączonego zarządzania cofaniem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795507"
---
# <a name="how-to-use-linked-undo-management"></a>Instrukcje: używanie dołączonego zarządzania cofaniem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Połączone cofnięcie umożliwia użytkownikowi jednoczesne cofnięcie tych samych zmian w wielu plikach. Na przykład jednoczesne zmiany tekstu między wieloma plikami programu, takimi jak plik nagłówka i plik Visual C++, to połączona transakcja cofania. Połączone funkcje cofania są wbudowane w implementację Menedżera cofania w środowisku i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> umożliwiają manipulowanie tą możliwością. Połączone operacje cofania są implementowane przez nadrzędną jednostkę cofania, która może łączyć oddzielne stosy cofania w celu traktowania jako pojedynczej jednostki cofania. Procedura używania połączonego polecenia Cofnij jest szczegółowo opisana w poniższej sekcji.  
  
### <a name="to-use-linked-undo"></a>Aby użyć połączonego polecenia Cofnij  
  
1. Zadzwoń `QueryService` na `SVsLinkedUndoManager` , aby uzyskać wskaźnik do `IVsLinkedUndoTransactionManager` .  
  
2. Utwórz początkową, połączoną jednostkę cofania, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Ustawia punkt początkowy dla zestawu stosów cofania, które mają być pogrupowane w połączone stosy cofania. W `OpenLinkedUndo` metodzie należy również określić, czy połączone cofnięcie ma być rygorystyczne czy nieścisłe. Nieścisłe połączone zachowanie operacji cofania oznacza, że niektóre dokumenty z połączonymi elementami równorzędnymi Cofnij mogą być zamknięte i nadal opuszczają inne połączone elementy równorzędne Cofnij na ich stosach. Ścisłe połączone zachowanie operacji cofania określa, że wszystkie połączone stosy akcji Cofnij muszą zostać cofnięte lub wcale. Dodaj kolejne połączone stosy cofania, wywołując metodę [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> , aby wycofać wszystkie połączone jednostki cofania jako jeden.  
  
    > [!NOTE]
    > Aby zaimplementować połączone zarządzanie Cofnij w edytorze, Dodaj polecenie Cofnij zarządzanie. Aby uzyskać więcej informacji na temat implementowania połączonego zarządzania cofaniem, zobacz [How to: Implementuj zarządzanie Cofnij](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Instrukcje: implementowanie zarządzania cofaniem](../extensibility/how-to-implement-undo-management.md)
