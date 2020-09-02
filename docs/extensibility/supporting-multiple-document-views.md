---
title: Obsługa widoków wielu dokumentów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699539"
---
# <a name="supporting-multiple-document-views"></a>Obsługa wielu widoków dokumentu
Można podać więcej niż jeden widok dokumentu, tworząc oddzielne dane dokumentu i obiekty widoku dokumentu dla edytora. Niektóre przypadki, w których będzie przydatny dodatkowy widok dokumentu, są następujące:

- Obsługa nowych okien: Edytor ma udostępniać dwa lub więcej widoków tego samego typu, tak aby użytkownik, który ma już otwarte okno w edytorze, mógł otworzyć nowe okno, wybierając polecenie **nowe okno** w menu **okno** .

- Obsługa formularzy i kodu: chcesz, aby Edytor zapewniał widoki różnych typów. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]na przykład program udostępnia widok formularza i widok kodu.

  Aby uzyskać więcej informacji na ten temat, zobacz procedurę metody CreateEditorInstance w pliku EditorFactory.cs w projekcie edytora niestandardowego utworzonym przez szablon pakietu programu Visual Studio. Aby uzyskać więcej informacji na temat tego projektu, zobacz [Przewodnik: Tworzenie niestandardowego edytora](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronizowanie widoków
 Podczas implementowania wielu widoków obiekt danych dokumentu jest odpowiedzialny za przechowywanie wszystkich widoków synchronizowanych z danymi. Korzystając z interfejsów obsługi zdarzeń, można <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> synchronizować wiele widoków z danymi.

 Jeśli nie używasz <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu do synchronizowania wielu widoków, musisz zaimplementować własny system zdarzeń do obsługi zmian wprowadzonych w obiekcie danych dokumentu. Aby zapewnić aktualność wielu widoków, można użyć różnych poziomów szczegółowości. Z ustawieniem maksymalnego stopnia szczegółowości podczas wpisywania w jednym widoku inne widoki są aktualizowane natychmiast. Przy minimalnym poziomie szczegółowości inne widoki nie są aktualizowane, dopóki nie zostaną aktywowane.

## <a name="determining-whether-document-data-is-already-open"></a>Określanie, czy dane dokumentu są już otwarte
 Uruchomiona tabela dokumentu (RDT) w zintegrowanym środowisku programistycznym (IDE) pomaga sprawdzić, czy dane dla dokumentu są już otwarte, jak pokazano na poniższym diagramie.

 ![Grafika DocDataView](../extensibility/media/docdataview.gif "Docdataview") Wiele widoków

 Domyślnie każdy widok (obiekt widoku dokumentu) jest zawarty w osobnym ramce okna ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ). Jak już zauważono, dane dokumentu mogą być wyświetlane w wielu widokach. Aby to umożliwić, program Visual Studio sprawdza RDT, aby określić, czy dokument jest już otwarty w edytorze. Gdy IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> do tworzenia edytora, wartość inna niż null zwracana w `punkDocDataExisting` parametrze wskazuje, że dokument jest już otwarty w innym edytorze. Aby uzyskać więcej informacji na temat sposobu działania funkcji RDT, zobacz [Uruchamianie tabeli dokumentów](../extensibility/internals/running-document-table.md).

 W Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementacji Sprawdź obiekt danych dokumentu zwrócony w, `punkDocDataExisting` Aby określić, czy dane dokumentu są odpowiednie dla edytora. (Na przykład tylko dane HTML powinny być wyświetlane przez Edytor HTML). Jeśli jest to odpowiednie, fabryka edytorów powinna udostępnić drugi widok danych. Jeśli `punkDocDataExisting` parametr nie jest `NULL` , możliwe jest, że obiekt danych dokumentu jest otwarty w innym edytorze lub, prawdopodobnie, że dane dokumentu są już otwarte w innym widoku z tym samym edytorem. Jeśli dane dokumentu są otwarte w innym edytorze, który nie jest obsługiwany przez fabrykę edytora, program Visual Studio nie może otworzyć fabryki edytora. Aby uzyskać więcej informacji, zobacz [How to: dołączanie widoków do danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md).
