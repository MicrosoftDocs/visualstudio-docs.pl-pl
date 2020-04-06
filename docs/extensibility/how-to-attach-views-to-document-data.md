---
title: 'Jak: Dołączanie widoków do danych dokumentu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711091"
---
# <a name="how-to-attach-views-to-document-data"></a>Jak: Dołączanie widoków do danych dokumentu
Jeśli masz nowy widok dokumentu, możesz dołączyć go do istniejącego obiektu danych dokumentu.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Aby ustalić, czy widok można dołączyć do istniejącego obiektu danych dokumentu

1. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>plik .

2. W implementacji `IVsEditorFactory::CreateEditorInstance`, `QueryInterface` wywołać istniejący obiekt danych `CreateEditorInstance` dokumentu, gdy IDE wywołuje implementacji.

    Wywołanie `QueryInterface` umożliwia sprawdzenie istniejącego obiektu danych dokumentu, `punkDocDataExisting` który jest określony w parametrze.

    Dokładne interfejsy, które należy zbadać, jednak zależy od edytora, który otwiera dokument, jak opisano w kroku 4.

3. Jeśli nie znajdziesz odpowiednich interfejsów na istniejącym obiekcie danych dokumentu, należy zwrócić do edytora kod błędu wskazujący, że obiekt danych dokumentu jest niezgodny z edytorem.

    W implementacji IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, okno komunikatu powiadamia, że dokument jest otwarty w innym edytorze i pyta, czy chcesz go zamknąć.

4. Jeśli zamkniesz ten dokument, program Visual Studio po raz drugi wywoła fabrykę edytora. W tym wywołaniu `DocDataExisting` parametr jest równy null. Implementacja fabryki edytora może następnie otworzyć obiekt danych dokumentu we własnym edytorze.

   > [!NOTE]
   > Aby ustalić, czy można pracować z istniejącym obiektem danych dokumentu, można również użyć [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] prywatnej wiedzy na temat implementacji interfejsu, rzucając wskaźnik do rzeczywistej klasy implementacji prywatnej. Na przykład wszystkie standardowe `IVsPersistFileFormat`edytory implementują , który dziedziczy po <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. W związku z `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>tym można wywołać , a jeśli identyfikator klasy na istniejącym obiekcie danych dokumentu odpowiada identyfikatorowi klasy implementacji, można pracować z obiektem danych dokumentu.

## <a name="robust-programming"></a>Solidne programowanie
 Gdy visual studio wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> implementacji metody, przekazuje z powrotem wskaźnik `punkDocDataExisting` do istniejącego obiektu danych dokumentu w parametrze, jeśli istnieje. Sprawdź obiekt danych dokumentu `punkDocDataExisting` zwrócony w celu ustalenia, czy obiekt danych dokumentu jest odpowiedni dla edytora, jak opisano w notatce w kroku 4 procedury w tym temacie. Jeśli jest to właściwe, fabryka edytora powinna zapewnić drugi widok danych, zgodnie z opisem w [pomocy technicznej wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md). Jeśli nie, powinien wyświetlić odpowiedni komunikat o błędzie.

## <a name="see-also"></a>Zobacz też
- [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)
- [Wyświetlanie danych i dokumentów w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)
