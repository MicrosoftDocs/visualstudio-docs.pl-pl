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
ms.openlocfilehash: ab033120c0913bbae33458c5a2d0b53972364581
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255767"
---
# <a name="access-data-in-documents-on-the-server"></a>Dostęp do danych w dokumentach na serwerze
  Można programować względem danych w dostosowaniu na poziomie dokumentu bez konieczności używania modelu obiektów programu Microsoft Office Word lub Microsoft Office Excel. Oznacza to, że można uzyskać dostęp do danych znajdujących się w dokumencie na serwerze, na którym nie zainstalowano programu Word lub Excel. Na przykład kod na serwerze (na [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] przykład na stronie) może dostosować dane w dokumencie i wysłać dostosowany dokument do użytkownika końcowego. Gdy użytkownik końcowy otworzy dokument, kod powiązania danych w zestawie rozwiązania wiąże dostosowane dane do dokumentu. Jest to możliwe, ponieważ dane w dokumencie są oddzielone od interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [buforowane dane w dostosowywaniu na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Dane pamięci podręcznej do użycia na serwerze
 Aby buforować obiekt danych w dokumencie, oznacz go <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutem w czasie projektowania lub `StartCaching` Użyj metody elementu hosta w czasie wykonywania. Gdy w dokumencie zostanie zbuforowany obiekt danych, obiekt zostanie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zserializowany do ciągu XML, który jest przechowywany w dokumencie. Obiekty muszą spełniać pewne wymagania, aby można było je zakwalifikować do buforowania. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

 Kod po stronie serwera może manipulować wszystkimi obiektami danych w pamięci podręcznej danych. Formanty, które są powiązane z buforowanymi wystąpieniami danych, są synchronizowane z interfejsem użytkownika, dzięki czemu wszystkie zmiany po stronie serwera, które są wprowadzane do danych są wyświetlane automatycznie po otwarciu dokumentu na kliencie.

## <a name="access-data-in-the-cache"></a>Dostęp do danych w pamięci podręcznej
 Dostęp do danych w pamięci podręcznej można uzyskać z aplikacji poza biurem, na przykład z poziomu aplikacji konsolowej, aplikacji Windows Forms lub strony sieci Web. Aplikacja, która uzyskuje dostęp do danych w pamięci podręcznej, musi mieć pełne zaufanie; Aplikacja sieci Web mająca częściowe zaufanie nie może wstawiać, pobierać ani zmieniać danych przechowywanych w pamięci podręcznej w dokumencie pakietu Office.

 Pamięć podręczna danych jest dostępna za pomocą hierarchii kolekcji, które są udostępniane przez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy:

- Właściwość zwraca obiekt <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, który zawiera wszystkie dane z pamięci podręcznej w dostosowaniu na poziomie dokumentu. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>

- Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> z nich zawiera co <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> najmniej jeden obiekt. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> Zawiera wszystkie obiekty danych w pamięci podręcznej, które są zdefiniowane w ramach pojedynczej klasy.

- Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> z nich zawiera co <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> najmniej jeden obiekt. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Reprezentuje pojedynczy obiekt danych w pamięci podręcznej.

  Poniższy przykład kodu demonstruje, jak uzyskać dostęp do buforowanego ciągu w `Sheet1` klasie projektu skoroszytu programu Excel. Ten przykład jest częścią większego przykładu przewidzianego dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modyfikowanie danych w pamięci podręcznej
 Aby zmodyfikować obiekt danych w pamięci podręcznej, należy zwykle wykonać następujące czynności:

1. Deserializować reprezentację XML obiektu w pamięci podręcznej do nowego wystąpienia obiektu. Dostęp do pliku XML można uzyskać przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwości <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , która reprezentuje obiekt danych w pamięci podręcznej.

2. Wprowadź zmiany w tej kopii.

3. Serializacja zmienionego obiektu z powrotem do pamięci podręcznej danych przy użyciu jednej z następujących opcji:

    - Jeśli chcesz automatycznie serializować zmiany, użyj <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody. Ta metoda używa formatu **DiffGram** do serializacji <xref:System.Data.DataSet>, <xref:System.Data.DataTable>i typy obiektów DataSet w pamięci podręcznej danych. Format **DiffGram** gwarantuje, że zmiany w pamięci podręcznej danych w dokumencie offline są wysyłane do serwera prawidłowo.

    - Jeśli chcesz wykonać własną serializację dla zmian danych w pamięci podręcznej, możesz pisać bezpośrednio do <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwości. Określ format **DiffGram** <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet>, jeśli używasz programu do aktualizowania bazy danych przy użyciu zmian wprowadzonych w danych w, <xref:System.Data.DataTable>lub z określonym zestawem danych. W przeciwnym razie zostanie zaktualizowana baza danych przez dodanie nowych wierszy zamiast modyfikowania istniejących wierszy. <xref:System.Data.Common.DataAdapter>

### <a name="modify-data-without-deserializing-the-current-value"></a>Modyfikuj dane bez deserializacji bieżącej wartości
 W niektórych przypadkach może zajść potrzeba zmodyfikowania wartości obiektu w pamięci podręcznej bez uprzedniego deserializacji bieżącej wartości. Na przykład możesz to zrobić, jeśli zmieniasz wartość obiektu, który ma typ prosty, taki jak ciąg lub liczba całkowita, lub jeśli inicjujesz buforowanie <xref:System.Data.DataSet> w dokumencie na serwerze. W takich przypadkach można użyć <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody bez uprzedniego deserializacji bieżącej wartości obiektu w pamięci podręcznej.

 Poniższy przykład kodu demonstruje, jak zmienić wartość buforowanego ciągu w `Sheet1` klasie projektu skoroszytu programu Excel. Ten przykład jest częścią większego przykładu przewidzianego dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modyfikowanie wartości null w pamięci podręcznej danych
 Pamięć podręczna danych nie przechowuje obiektów, które mają wartość **null** , gdy dokument jest zapisywany i zamykany. To ograniczenie ma kilka konsekwencji w przypadku modyfikacji danych w pamięci podręcznej:

- Jeśli ustawisz dowolny obiekt w pamięci podręcznej danych na wartość **null**, wszystkie obiekty w pamięci podręcznej danych zostaną automatycznie ustawione na **wartość null** , gdy dokument zostanie otwarty, a cała pamięć podręczna danych zostanie wyczyszczona, gdy dokument zostanie zapisany i zamknięty. Oznacza to, że wszystkie obiekty w pamięci podręcznej zostaną usunięte z pamięci podręcznej <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> danych, a kolekcja będzie pusta.

- Jeśli tworzysz rozwiązanie z **pustymi** obiektami w pamięci podręcznej danych i chcesz zainicjować te obiekty przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy przed otwarciem dokumentu po raz pierwszy, musisz się upewnić, że zainicjowano wszystkie obiekty w pamięci podręcznej danych. Jeśli zainicjujesz tylko niektóre z obiektów, wszystkie obiekty zostaną ustawione na **wartość null** , gdy dokument zostanie otwarty, a cała pamięć podręczna danych zostanie wyczyszczona po zapisaniu i zamknięciu dokumentu.

## <a name="access-typed-datasets-in-the-cache"></a>Dostęp do wpisanych zestawów danych w pamięci podręcznej
 Jeśli chcesz uzyskać dostęp do danych w określonym zestawie danych zarówno z rozwiązania pakietu Office, jak i z aplikacji poza biurem, na przykład aplikacji Windows Forms lub [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projektu, musisz zdefiniować określony zestaw danych w osobnym zestawie, do którego istnieje odwołanie w obu projektami. W przypadku dodania określonego zestawu danych do każdego projektu przy użyciu kreatora **konfiguracji źródła danych** lub **Projektant obiektów DataSet**, .NET Framework będzie traktować typy zestawów danych w dwóch projektach jako różne. Aby uzyskać więcej informacji o tworzeniu wpisanych zestawów danych, zobacz [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Dane w pamięci podręcznej w dostosowaniu na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)