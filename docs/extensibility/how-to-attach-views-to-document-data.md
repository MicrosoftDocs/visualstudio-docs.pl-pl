---
title: 'Instrukcje: Dołączanie widoków do danych dokumentów | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38818faa83f1fe901c5c3b19786aff8b3935f3b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870102"
---
# <a name="how-to-attach-views-to-document-data"></a>Instrukcje: Dołączanie widoków do danych dokumentu
Jeśli masz nowy widok dokumentu, można dołączyć do istniejącego obiektu danych dokumentu.  
  
## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Aby określić, jeśli widok można dołączyć do istniejącego obiektu danych dokumentu  
  
1. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. W danej implementacji `IVsEditorFactory::CreateEditorInstance`, wywołaj `QueryInterface` na istniejący obiekt danych dokumentu, gdy wywołuje IDE swoje `CreateEditorInstance` implementacji.  
  
    Wywoływanie `QueryInterface` umożliwia zbadanie istniejący obiekt danych dokumentu, którą określono w `punkDocDataExisting` parametru.  
  
    Dokładne interfejsy, które musisz wykonać kwerendę zależy edytor, który jest otwarcie dokumentu, jednak zgodnie z opisem w kroku 4.  
  
3. Jeśli nie znajdziesz odpowiednich interfejsów na istniejący obiekt danych dokumentów, zwracają kod błędu do edytora wskazujący, że obiekt danych dokumentu jest niezgodna z edytora.  
  
    W implementacji środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, okno komunikatu informuje, że dokument jest otwarty w innym edytorze i pyta, czy go zamknąć.  
  
4. Jeśli ten dokument zostanie zamknięty, program Visual Studio wywołuje fabryką edytora raz drugi. W tym wywołaniu `DocDataExisting` parametr jest równy NULL. Wdrożenie fabryki edytora można otworzyć obiektu danych dokumentu w edytorze własne.  
  
   > [!NOTE]
   >  Aby ustalić, czy można pracować z istniejącego obiektu danych dokumentów, umożliwia również prywatne znajomości implementacji interfejsu przez rzutowanie wskaźnika do rzeczywistej [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] klasy implementacja prywatna. Na przykład zaimplementować wszystkich standardowych edytorów `IVsPersistFileFormat`, który dziedziczy z <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. W związku z tym, można wywołać `QueryInterface` dla <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, i czy identyfikator klasy na istniejący obiekt dokumentu w danych odpowiada Twoja implementacja identyfikator klasy, a następnie można pracować z obiektem danych dokumentu.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Gdy program Visual Studio wywołuje implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody przekazuje powrót wskaźnika do istniejącego obiektu danych dokumentu w `punkDocDataExisting` parametru, jeśli taki istnieje. Sprawdź obiekt danych dokumentu, które są zwracane w `punkDocDataExisting` do ustalenia, czy obiekt danych dokumentu jest odpowiednie dla Twojego edytora, zgodnie z opisem w Uwaga w kroku 4 procedury przedstawione w tym temacie. Jeśli jest odpowiednia, a następnie fabryką edytora powinien zapewnić drugi widok danych zgodnie z opisem w [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md). Jeśli nie, następnie powinna zostać wyświetlona odpowiedni komunikat o błędzie.  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Dane dokumentu i Widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)