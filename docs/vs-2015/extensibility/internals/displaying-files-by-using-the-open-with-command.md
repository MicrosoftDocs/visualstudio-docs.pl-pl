---
title: Wyświetlanie plików za pomocą polecenia Otwórz za pomocą polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 716e9f1551681b9e194bd300522f55ab5e927dab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816461"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekt można zadawać IDE, aby wyświetlić **Otwórz za pomocą** okno dialogowe. To żądanie monituje użytkownika o otwarcie pliku, który zawiera szereg standardowych edytorów. W poniższych krokach opisano tego procesu.  
  
1.  Wywoływanych w projekcie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, określając wartość OSE_UseOpenWithDialog dla `OSEOpenDocEditor` parametru.  
  
2.  Oparte na rozszerzenie nazwy pliku dokumentu, IDE określa edytory, które się na liście mogą rejestru Otwórz określony dokument i wyświetla te informacje w **Otwórz za pomocą** okno dialogowe.  
  
    > [!NOTE]
    >  Projekty, które mają wewnętrzne edytor, który musi być uwzględniona w **Otwórz za pomocą** okno dialogowe, należy zarejestrować fabryki edytora dla każdego takiego edytora. Edytory wewnętrzne tylko funkcji wraz z określonego typu projektu, który jest wymuszany w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. IDE ma fabrykę wbudowanego edytora podstawowy edytor tekstu i edytorze binarnym. IDE również tworzy wystąpienie fabryki edytora imieniu każdego zarejestrowane skojarzenie pliku Windows. Przykładem takiego pliku jest program Microsoft Word.  
  
3.  Zaraz po użytkownik wybierze element **Otwórz za pomocą** dokument zostanie otwarte okno dialogowe, następnie IDE, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)

