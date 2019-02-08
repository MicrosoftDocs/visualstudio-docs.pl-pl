---
title: Dostęp do danych w dokumentach na serwerze
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d13a15386fe8486dae16173ebb52ec2593de24f5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926856"
---
# <a name="access-data-in-documents-on-the-server"></a>Dostęp do danych w dokumentach na serwerze
  Można programować względem danych w dostosowaniu na poziomie dokumentu, bez konieczności używania modelu obiektów programu Microsoft Office Word lub Microsoft Office Excel. Oznacza to, że można dostęp do danych znajdujących się w dokumencie na serwerze, który nie ma programu Word lub programem Excel zainstalowanym. Na przykład kod na serwerze (na przykład w [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony) można dostosować dane w dokumencie i dostosowany dokument wysyłany do użytkownika końcowego. Po otwarciu dokumentu przez użytkownika końcowego dostosowanych danych Kod powiązania danych w zestawie rozwiązania wiąże się z dokumentem. Jest to możliwe, ponieważ dane w dokumencie są oddzielone od interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [dane dostosowywane na poziomie dokumentu z pamięci podręcznej](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Dane do użycia na serwerze z pamięci podręcznej
 Buforowanie obiektu danych w dokumencie, oznacz go za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu w czasie projektowania lub użyj `StartCaching` metoda elementu hosta w czasie wykonywania. Gdy buforowanie obiektu danych w dokumencie, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializuje obiekt do ciągu XML, który znajduje się w dokumencie. Obiekty muszą spełniać określone wymagania, aby zakwalifikować się do buforowania. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).

 Kod po stronie serwera można manipulować żadnych obiektów danych w pamięci podręcznej danych. Formanty powiązane z wystąpieniami dane w pamięci podręcznej są synchronizowane z interfejsu użytkownika, tak, aby wszelkie zmiany po stronie serwera, które zostały wprowadzone dane będą automatycznie wyświetlane po otwarciu dokumentu na komputerze klienckim.

## <a name="access-data-in-the-cache"></a>Dostęp do danych w pamięci podręcznej
 Można uzyskać dostęp do danych w pamięci podręcznej z poziomu aplikacji poza biurem, np. z aplikacji konsoli, aplikacji programu Windows Forms lub strony sieci Web. Aplikacja, która uzyskuje dostęp do pamięci podręcznej danych musi mieć pełne zaufanie; Aplikacja sieci Web, która ma częściowej relacji zaufania nie można wstawić, pobrać lub zmienić dane, które są buforowane w dokumencie programu Word.

 Pamięć podręczna danych jest dostępny za pośrednictwem hierarchii kolekcje są udostępniane przez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy:

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Właściwość zwraca <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, który zawiera wszystkie buforowane dane w dostosowaniu na poziomie dokumentu.

- Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> zawiera jeden lub więcej <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obiektów. Element <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> zawiera wszystkie obiekty danych w pamięci podręcznej, które są zdefiniowane w ramach jednej klasy.

- Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> zawiera jeden lub więcej <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> obiektów. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> reprezentuje obiekt pojedynczego dane w pamięci podręcznej.

  Poniższy przykład kodu demonstruje sposób dostępu ciąg w pamięci podręcznej w `Sheet1` klasy projektu skoroszytu programu Excel. W tym przykładzie jest częścią większego przykładu, który jest udostępniany dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modyfikowanie danych w pamięci podręcznej
 Aby zmodyfikować obiekt dane w pamięci podręcznej, zwykle wykonują następujące czynności:

1.  Deserializuje reprezentację XML obiektu w pamięci podręcznej do nowego wystąpienia obiektu. Dostęp do pliku XML przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> reprezentujący obiekt dane w pamięci podręcznej.

2.  Wprowadź zmiany w tej kopii.

3.  Serializowanie zmienionych obiektów do pamięci podręcznej danych przy użyciu jednej z następujących opcji:

    -   Jeśli chcesz automatycznie serializuj zmiany, należy użyć <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody. Ta metoda używa **w formacie DiffGram** format serializacji <xref:System.Data.DataSet>, <xref:System.Data.DataTable>i wpisana zestawu danych obiektów w pamięci podręcznej danych. **w formacie DiffGram** format gwarantuje, że zmiany w pamięci podręcznej danych w dokumencie w trybie offline są prawidłowo wysyłane do serwera.

    -   Jeśli chcesz wykonać swoje własne serializacji zmian danych w pamięci podręcznej, można napisać bezpośrednio do <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwości. Określ **w formacie DiffGram** formatu, jeśli używasz <xref:System.Data.Common.DataAdapter> aktualizacji bazy danych za pomocą zmian wprowadzonych w danych w <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub typizowany zestaw danych. W przeciwnym razie <xref:System.Data.Common.DataAdapter> spowoduje zaktualizowanie bazy danych, dodając nowe wiersze zamiast modyfikowania istniejących wierszy.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modyfikowanie danych bez deserializacja bieżącą wartość
 W niektórych przypadkach możesz chcieć zmodyfikować wartość obiektu w pamięci podręcznej nie pierwszy deserializacja bieżącą wartość. Na przykład, można to zrobić w przypadku zmiany wartości obiektu, który jest typem prostym, takie jak ciąg lub liczba całkowita, czy są inicjowanie pamięci podręcznej <xref:System.Data.DataSet> w dokumencie na serwerze. W takich przypadkach można użyć <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody bez pierwszy deserializacja bieżącą wartość obiektu w pamięci podręcznej.

 Poniższy przykład kodu pokazuje, jak zmienić wartość ciąg w pamięci podręcznej w `Sheet1` klasy projektu skoroszytu programu Excel. W tym przykładzie jest częścią większego przykładu, który jest udostępniany dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modyfikowanie wartości null w pamięci podręcznej danych
 Pamięć podręczna danych nie są zapisywane obiekty, które mają wartość **null** gdy dokument zostanie zapisany i zamknięte. To ograniczenie ma kilka konsekwencje modyfikacji danych w pamięci podręcznej:

-   Jeśli ustawisz dowolnego obiektu w pamięci podręcznej danych na wartość **null**, wszystkie obiekty w pamięci podręcznej danych zostanie automatycznie ustawiony w **null** po otwarciu dokumentu i pamięci podręcznej danych całej zostanie wyczyszczona podczas dokument jest zapisać i zamknąć. Oznacza to, że wszystkie obiekty w pamięci podręcznej zostaną usunięte z pamięci podręcznej danych i <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> kolekcja będzie pusta.

-   W przypadku tworzenia rozwiązania przy użyciu **null** obiektów w pamięci podręcznej danych i chcesz zainicjować tych obiektów za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy przed dokument zostanie otwarty po raz pierwszy, należy upewnić się, zainicjuj wszystkie obiekty w pamięci podręcznej danych. Jeśli można zainicjować tylko niektórych obiektów, wszystkie obiekty zostanie ustawiona **null** po otwarciu dokumentu i pamięci podręcznej wszystkie dane zostaną wyczyszczone, gdy dokument zostanie zapisany i zamknięte.

## <a name="access-typed-datasets-in-the-cache"></a>Dostęp wpisanych zestawów danych w pamięci podręcznej
 Jeśli chcesz uzyskać dostęp do danych w zestawie danych wpisywanych, zarówno z rozwiązania do pakietu Office i aplikacji poza biurem, takich jak aplikacji Windows Forms lub [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projektu, należy zdefiniować typizowany zestaw danych w osobnym zestawie, który odwołuje się do obu projekty. Jeśli dodasz typizowany zestaw danych do każdego projektu za pomocą **konfiguracji źródła danych** kreatora lub **Projektanta obiektów Dataset**, .NET Framework będą traktować typizowanych zestawów danych w dwóch projektów jako różne typy . Aby uzyskać więcej informacji na temat tworzenia typizowanych zestawów danych, zobacz [tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Dane w pamięci podręcznej dostosowywane na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)