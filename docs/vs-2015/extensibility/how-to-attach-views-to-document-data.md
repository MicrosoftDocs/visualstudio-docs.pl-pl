---
title: 'Instrukcje: Dołączanie widoków do danych dokumentów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 671a243f65c68660c98c3730ca90568882a824d6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755609"
---
# <a name="how-to-attach-views-to-document-data"></a>Instrukcje: Dołączanie widoków do danych dokumentów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli masz nowy widok dokumentu, można dołączyć do istniejącego obiektu danych dokumentu.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Aby określić, jeśli widok można dołączyć do istniejącego obiektu danych dokumentu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  W danej implementacji `IVsEditorFactory::CreateEditorInstance`, wywołaj `QueryInterface` na istniejący obiekt danych dokumentu, gdy wywołuje IDE swoje `CreateEditorInstance` implementacji.  
  
     Wywoływanie `QueryInterface` umożliwia zbadanie istniejący obiekt danych dokumentu, którą określono w `punkDocDataExisting` parametru.  
  
     Dokładne interfejsy, które musisz wykonać kwerendę zależy edytor, który jest otwarcie dokumentu, jednak zgodnie z opisem w kroku 4.  
  
3.  Jeśli nie znajdziesz odpowiednich interfejsów na istniejący obiekt danych dokumentów, zwracają kod błędu do edytora wskazujący, że obiekt danych dokumentu jest niezgodna z edytora.  
  
     W implementacji środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, okno komunikatu informuje, że dokument jest otwarty w innym edytorze i pyta, czy go zamknąć.  
  
4.  Jeśli ten dokument zostanie zamknięty, program Visual Studio wywołuje fabryką edytora raz drugi. W tym wywołaniu `DocDataExisting` parametr jest równy NULL. Wdrożenie fabryki edytora można otworzyć obiektu danych dokumentu w edytorze własne.  
  
    > [!NOTE]
    >  Aby ustalić, czy można pracować z istniejącego obiektu danych dokumentów, umożliwia również prywatne znajomości implementacji interfejsu przez rzutowanie wskaźnika do rzeczywistej [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] klasy implementacja prywatna. Na przykład zaimplementować wszystkich standardowych edytorów `IVsPersistFileFormat`, który dziedziczy z <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. W związku z tym, można wywołać `QueryInterface` dla <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, i czy identyfikator klasy na istniejący obiekt dokumentu w danych odpowiada Twoja implementacja identyfikator klasy, a następnie można pracować z obiektem danych dokumentu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Gdy program Visual Studio wywołuje implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody przekazuje powrót wskaźnika do istniejącego obiektu danych dokumentu w `punkDocDataExisting` parametru, jeśli taki istnieje. Sprawdź obiekt danych dokumentu, które są zwracane w `punkDocDataExisting` do ustalenia, czy obiekt danych dokumentu jest odpowiednie dla Twojego edytora, zgodnie z opisem w Uwaga w kroku 4 procedury przedstawione w tym temacie. Jeśli jest odpowiednia, a następnie fabryką edytora powinien zapewnić drugi widok danych zgodnie z opisem w [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md). Jeśli nie, następnie powinna zostać wyświetlona odpowiedni komunikat o błędzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)
