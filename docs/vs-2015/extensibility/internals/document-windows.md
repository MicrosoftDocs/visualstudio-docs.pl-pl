---
title: Okna dokumentów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791113"
---
# <a name="document-windows"></a>Okna dokumentów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W programie Visual Studio *okno dokumentu* jest oknem podrzędnym z ramkami, które jest skojarzone z oknem interfejsu wielu dokumentów (MDI). Okna dokumentów są zwykle używane do wyświetlania i modyfikacji kodu źródłowego lub tekstu, ale mogą również hostować inne typy funkcjonalne. Okna dokumentów:  
  
- Może być zorganizowany w oddzielnych lub pionowych grupach kart w nadrzędnym pliku MDI, aby można było przeglądać wiele plików jednocześnie.  
  
- Można zadokować w dowolnej kolejności w nadrzędnym MDI.  
  
- Mogą być swobodne.  
  
- Są połączone w kolejności tabulacji z innymi oknami MDI.  
  
  Polecenia służące do grupowania, dokowania i zmiennoprzecinkowej można znaleźć w menu skrótów dla karty okna dokumentu.  
  
  Aby uzyskać więcej informacji na temat zachowania okna w programie Visual Studio, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementacja okna dokumentu  
 Okna dokumentów są tworzone przez implementację edytora. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Interfejs tworzy okna dokumentów w ramach tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [starsze interfejsy w edytorze](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
> Aby zapewnić punkty nawigacji do tyłu i do przodu w oknie, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfejs. Edytor tekstu używa znaczników tekstowych do identyfikowania punktów nawigacji w dokumencie.  
  
## <a name="the-running-document-table"></a>Uruchomiona tabela dokumentów  
 IDE korzysta z uruchomionej tabeli dokumentu (RDT) w celu śledzenia stanu każdego okna dokumentu. RDT jest mechanizmem, za pomocą którego okna dokumentów są powiadamiane o zdarzeniach, na przykład po zamknięciu rozwiązania lub edytowaniu pliku. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opóźnione ładowanie dokumentu](../../extensibility/internals/delayed-document-loading.md)
