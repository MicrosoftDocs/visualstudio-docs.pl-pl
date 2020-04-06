---
title: Obsługa wielu widoków dokumentu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699539"
---
# <a name="supporting-multiple-document-views"></a>Obsługa wielu widoków dokumentu
Można podać więcej niż jeden widok dokumentu, tworząc oddzielne obiekty danych dokumentu i widoku dokumentu dla edytora. W niektórych przypadkach przydatne byłoby dodatkowe wyświetlanie dokumentu:

- Obsługa nowego okna: Chcesz, aby edytor udostępniał dwa lub więcej widoków tego samego typu, dzięki czemu użytkownik, który ma już otwarte okno w edytorze, może otworzyć nowe okno, wybierając polecenie **Nowe okno** z menu **Okno.**

- Obsługa widoku formularzy i kodu: chcesz, aby edytor udostępniał widoki różnych typów. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], na przykład zapewnia zarówno widok formularza, jak i widok kodu.

  Aby uzyskać więcej informacji na ten temat, zobacz CreateEditorInstance procedury w pliku EditorFactory.cs w projekcie edytora niestandardowego utworzonego przez szablon pakietu programu Visual Studio. Aby uzyskać więcej informacji na temat tego projektu, zobacz [Przewodnik: Tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronizowanie widoków
 Podczas implementowania wielu widoków obiekt danych dokumentu jest odpowiedzialny za utrzymywanie wszystkich widoków zsynchronizowanych z danymi. Interfejsy obsługi zdarzeń można <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> użyć do synchronizacji wielu widoków z danymi.

 Jeśli <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiekt nie jest używany do synchronizowania wielu widoków, należy zaimplementować własny system zdarzeń do obsługi zmian wprowadzonych w obiekcie danych dokumentu. Można użyć różnych poziomów szczegółowości, aby zachować wiele widoków na bieżąco. Przy ustawieniu maksymalnej szczegółowości, podczas wpisywać w jednym widoku, inne widoki są aktualizowane natychmiast. Przy minimalnej szczegółowości inne widoki nie są aktualizowane, dopóki nie zostaną aktywowane.

## <a name="determining-whether-document-data-is-already-open"></a>Określanie, czy dane dokumentu są już otwarte
 Uruchomiona tabela dokumentów (RDT) w zintegrowanym środowisku programistycznym (IDE) pomaga śledzić, czy dane dla dokumentu są już otwarte, jak pokazano na poniższym diagramie.

 ![Grafika DocDataView](../extensibility/media/docdataview.gif "Docdataview") Wiele widoków

 Domyślnie każdy widok (obiekt widoku dokumentu) znajduje się<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>we własnej ramce okna ( ). Jak już wspomniano, jednak dane dokumentu mogą być wyświetlane w wielu widokach. Aby włączyć tę funkcję, visual studio sprawdza RDT, aby ustalić, czy dany dokument jest już otwarty w edytorze. Gdy IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> wywołuje utworzenie edytora, wartość inna niż `punkDocDataExisting` NULL zwrócona w parametrze wskazuje, że dokument jest już otwarty w innym edytorze. Aby uzyskać więcej informacji na temat funkcjonowania RDT, zobacz [Uruchamianie tabeli dokumentów](../extensibility/internals/running-document-table.md).

 W <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementacji sprawdź obiekt danych `punkDocDataExisting` dokumentu zwrócony w celu ustalenia, czy dane dokumentu są odpowiednie dla edytora. (Na przykład edytor HTML powinien wyświetlać tylko dane HTML). Jeśli jest to właściwe, fabryka edytora powinna zapewnić drugi widok danych. Jeśli `punkDocDataExisting` parametr nie `NULL`jest , jest możliwe, że obiekt danych dokumentu jest otwarty w innym edytorze, lub, bardziej prawdopodobne, że dane dokumentu jest już otwarty w innym widoku z tym samym edytorem. Jeśli dane dokumentu jest otwarty w innym edytorze, że fabryka edytora nie obsługuje, a następnie visual studio nie można otworzyć fabryki edytora. Aby uzyskać więcej informacji, zobacz [Jak: Dołączanie widoków do danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md).
