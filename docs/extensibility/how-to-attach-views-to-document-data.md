---
title: 'Instrukcje: dołączanie widoków do danych dokumentu | Microsoft Docs'
description: Może być możliwe dołączenie nowego widoku dokumentu do istniejącego obiektu danych dokumentu. Użyj tej procedury, aby określić, czy można dołączyć widok.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e044ecbf2309d4d858c16afbdddc130b4661005
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994189"
---
# <a name="how-to-attach-views-to-document-data"></a>Instrukcje: dołączanie widoków do danych dokumentu
Jeśli masz nowy widok dokumentu, może być możliwe dołączenie go do istniejącego obiektu danych dokumentu.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Aby określić, czy można dołączyć widok do istniejącego obiektu danych dokumentu

1. Implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .

2. W implementacji programu `IVsEditorFactory::CreateEditorInstance` Zadzwoń `QueryInterface` na istniejący obiekt danych dokumentu, gdy IDE wywoła `CreateEditorInstance` implementację.

    Wywołanie `QueryInterface` umożliwia badanie istniejącego obiektu danych dokumentu, który jest określony w `punkDocDataExisting` parametrze.

    Dokładne interfejsy, które należy wykonać, są jednak zależne od edytora otwierającego dokument, jak opisano w kroku 4.

3. Jeśli nie znajdziesz odpowiednich interfejsów w istniejącym obiekcie danych dokumentu, zwróć kod błędu do edytora, wskazując, że obiekt danych dokumentu jest niezgodny z edytorem.

    W implementacji środowiska IDE w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oknie komunikatu zostanie wyświetlony komunikat z informacją o tym, że dokument jest otwarty w innym edytorze i pyta, czy chcesz go zamknąć.

4. W przypadku zamknięcia tego dokumentu program Visual Studio wywołuje fabrykę edytora po raz drugi. W przypadku tego wywołania `DocDataExisting` parametr jest równy null. Implementacja fabryki edytora może następnie otworzyć obiekt danych dokumentu w Twoim edytorze.

   > [!NOTE]
   > Aby określić, czy można współpracować z istniejącym obiektem danych dokumentu, można również użyć prywatnej znajomości implementacji interfejsu przez rzutowanie wskaźnika do rzeczywistej [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] klasy implementacji prywatnej. Na przykład wszystkie standardowe edytory implementują `IVsPersistFileFormat` , która dziedziczy z <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . W ten sposób można wywołać `QueryInterface` dla <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> , a jeśli identyfikator klasy w istniejącym obiekcie danych dokumentu jest zgodny z identyfikatorem klasy implementacji, można współpracować z obiektem danych dokumentu.

## <a name="robust-programming"></a>Niezawodne programowanie
 Gdy program Visual Studio wywołuje implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, przekazuje wskaźnik do istniejącego obiektu danych dokumentu w `punkDocDataExisting` parametrze, jeśli taki istnieje. Sprawdź obiekt danych dokumentu zwrócony w programie, `punkDocDataExisting` Aby określić, czy obiekt danych dokumentu jest odpowiedni dla edytora, jak opisano w sekcji Krok 4 procedury w tym temacie. Jeśli jest to odpowiednie, fabryka edytorów powinna udostępnić drugi widok danych, jak opisano w temacie [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md). W przeciwnym razie powinien zostać wyświetlony odpowiedni komunikat o błędzie.

## <a name="see-also"></a>Zobacz też
- [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md)
- [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)
