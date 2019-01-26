---
title: Wyświetlanie plików za pomocą polecenia Otwórz za pomocą polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a101f59615c29499905fee9bef1249b399a573e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951043"
---
# <a name="display-files-by-using-the-open-with-command"></a>Wyświetlanie plików za pomocą polecenia Otwórz za pomocą
Projekt można zadawać IDE, aby wyświetlić **Otwórz za pomocą** okno dialogowe. To żądanie monituje użytkownika o otwarcie pliku, który zawiera szereg standardowych edytorów. W poniższych krokach opisano tego procesu:  
  
1.  Wywoływanych w projekcie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, określając wartość `OSE_UseOpenWithDialog` dla `OSEOpenDocEditor` parametru.  
  
2.  Oparte na rozszerzenie nazwy pliku dokumentu, IDE określa edytory, które się na liście mogą rejestru Otwórz określony dokument i wyświetla te informacje w **Otwórz za pomocą** okno dialogowe.  
  
    > [!NOTE]
    >  Projekty, które mają wewnętrzne edytor, który musi być uwzględniona w **Otwórz za pomocą** okno dialogowe, należy zarejestrować fabryki edytora dla każdego takiego edytora. Edytory wewnętrzne tylko funkcji wraz z określonego typu projektu, który jest wymuszany w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. IDE ma fabrykę wbudowanego edytora podstawowy edytor tekstu i edytorze binarnym. IDE również tworzy wystąpienie fabryki edytora imieniu każdego zarejestrowane skojarzenie pliku Windows. Przykładem takiego pliku jest program Microsoft Word.  
  
3.  Zaraz po użytkownik wybierze element **Otwórz za pomocą** dokument zostanie otwarte okno dialogowe, następnie IDE, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Instrukcje: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)
