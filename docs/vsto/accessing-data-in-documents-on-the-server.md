---
title: Uzyskiwanie dostępu do danych w dokumentach na serwerze
description: Dowiedz się, jak programować względem danych w dostosowywaniu na poziomie dokumentu bez konieczności używania modelu obiektów programu Microsoft Office Word lub Microsoft Office Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0df6aef3c83d66b84f569e85e953fde8a3f0e16c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826775"
---
# <a name="access-data-in-documents-on-the-server"></a>Uzyskiwanie dostępu do danych w dokumentach na serwerze
  Możesz programować względem danych w dostosowywaniu na poziomie dokumentu bez konieczności używania modelu obiektów programu Microsoft Office Word lub Microsoft Office Excel. Oznacza to, że możesz uzyskać dostęp do danych zawartych w dokumencie na serwerze, na którym nie zainstalowano programu Word ani Excel. Na przykład kod na serwerze (na przykład na stronie) może dostosować dane w dokumencie i wysłać dostosowany dokument [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] do użytkownika końcowego. Gdy użytkownik końcowy otworzy dokument, kod powiązania danych w zestawie rozwiązania wiąże dostosowane dane z dokumentem. Jest to możliwe, ponieważ dane w dokumencie są oddzielone od interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Cached data in document-level customizations (Buforowane dane w dostosowaniach na poziomie dokumentu).](../vsto/cached-data-in-document-level-customizations.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Dane pamięci podręcznej do użycia na serwerze
 Aby buforować obiekt danych w dokumencie, oznacz go atrybutem w czasie projektowania lub użyj metody elementu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> `StartCaching` hosta w czasie działania. Podczas buforowania obiektu danych w dokumencie obiekt serializuje go do ciągu XML przechowywanego [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] w dokumencie. Obiekty muszą spełniać pewne wymagania, aby kwalifikowały się do buforowania. Aby uzyskać więcej informacji, zobacz [Dane pamięci podręcznej](../vsto/caching-data.md).

 Kod po stronie serwera może manipulować dowolnymi obiektami danych w pamięci podręcznej danych. Kontrolki powiązane z wystąpieniami danych w pamięci podręcznej są synchronizowane z interfejsem użytkownika, dzięki czemu wszelkie zmiany wprowadzone w danych po stronie serwera są automatycznie wyświetlane po otwarciu dokumentu na kliencie.

## <a name="access-data-in-the-cache"></a>Uzyskiwanie dostępu do danych w pamięci podręcznej
 Dostęp do danych w pamięci podręcznej można uzyskać z aplikacji spoza pakietu Office, na przykład z aplikacji konsolowej, aplikacji Windows Forms aplikacji lub strony internetowej. Aplikacja, która uzyskuje dostęp do buforowanych danych, musi mieć pełne zaufanie; Aplikacja internetowa, która ma częściowe zaufanie, nie może wstawiać, pobierać ani zmieniać danych buforowanych w dokumencie pakietu Office.

 Pamięć podręczna danych jest dostępna za pośrednictwem hierarchii kolekcji, które są udostępniane <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> przez właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy :

- Właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> zwraca <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> obiekt , który zawiera wszystkie buforowane dane w dostosowywaniu na poziomie dokumentu.

- Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> obiekt zawiera co najmniej jeden <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obiekt. Obiekt <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> zawiera wszystkie obiekty danych w pamięci podręcznej, które są zdefiniowane w ramach jednej klasy.

- Każdy <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> obiekt zawiera co najmniej jeden <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> obiekt. Reprezentuje <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> pojedynczy obiekt danych w pamięci podręcznej.

  W poniższym przykładzie kodu pokazano, jak uzyskać dostęp do buforowanych ciągów `Sheet1` w klasie projektu skoroszytu programu Excel. Ten przykład jest częścią większego przykładu, który jest dostarczany dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody .

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Modyfikowanie danych w pamięci podręcznej
 Aby zmodyfikować obiekt danych w pamięci podręcznej, zazwyczaj należy wykonać następujące czynności:

1. Deserializuj reprezentację XML obiektu w pamięci podręcznej do nowego wystąpienia obiektu. Dostęp do kodu XML można uzyskać za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwości , która reprezentuje obiekt danych w pamięci <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> podręcznej.

2. Dokonaj zmian w tej kopii.

3. Serializuj zmieniony obiekt z powrotem do pamięci podręcznej danych przy użyciu jednej z następujących opcji:

    - Jeśli chcesz automatycznie serializować zmiany, użyj <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody . Ta metoda używa formatu **DiffGram** do serializacji <xref:System.Data.DataSet> obiektów , i typizowanych zestawów danych w pamięci <xref:System.Data.DataTable> podręcznej danych. Format **DiffGram zapewnia,** że zmiany w pamięci podręcznej danych w dokumencie w trybie offline są prawidłowo wysyłane do serwera.

    - Jeśli chcesz wykonać własną serializacji dla zmian w pamięci podręcznej danych, można zapisać bezpośrednio do <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> właściwości. Określ format **DiffGram,** jeśli używasz obiektu do aktualizowania bazy danych za pomocą zmian wprowadzonych w danych w <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet> <xref:System.Data.DataTable> typiowym zestawie danych , lub . W przeciwnym razie <xref:System.Data.Common.DataAdapter> baza danych zostanie zaktualizowana przez dodanie nowych wierszy zamiast modyfikowania istniejących wierszy.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modyfikowanie danych bez deserializacji bieżącej wartości
 W niektórych przypadkach można zmodyfikować wartość obiektu pamięci podręcznej bez uprzedniego deserializacji bieżącej wartości. Można to zrobić na przykład w przypadku zmiany wartości obiektu o prostym typie, takim jak ciąg lub liczba całkowita, lub w przypadku inicjowania buforowanej w dokumencie na <xref:System.Data.DataSet> serwerze. W takich przypadkach można użyć metody <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> bez uprzedniego deserializacji bieżącej wartości obiektu w pamięci podręcznej.

 Poniższy przykład kodu pokazuje, jak zmienić wartość buforowanych ciągów w `Sheet1` klasie projektu skoroszytu programu Excel. Ten przykład jest częścią większego przykładu dostarczonego dla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metody .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Modyfikowanie wartości null w pamięci podręcznej danych
 Pamięć podręczna danych nie przechowuje obiektów o wartości **null** po zapisaniu i zamknięciu dokumentu. To ograniczenie ma kilka konsekwencji podczas modyfikowania danych w pamięci podręcznej:

- Jeśli dowolny obiekt w pamięci podręcznej danych zostanie ustawiony na wartość **null,** wszystkie obiekty w pamięci podręcznej danych zostaną automatycznie ustawione na wartość **null** po otwarciu dokumentu, a cała pamięć podręczna danych zostanie wyczyszona po zapisaniu i zamknięciu dokumentu. Oznacza to, że wszystkie buforowane obiekty zostaną usunięte z pamięci podręcznej danych, a kolekcja <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> będzie pusta.

- Jeśli tworzysz rozwiązanie z obiektami o wartości **null** w pamięci podręcznej danych i chcesz zainicjować te obiekty przy użyciu klasy przed pierwszym otwarciem dokumentu, musisz się upewnić, że wszystkie obiekty w pamięci podręcznej danych są <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> zainicjowane. W przypadku zainicjowania tylko niektórych obiektów wszystkie obiekty zostaną ustawione na wartość **null** po otwarciu dokumentu, a cała pamięć podręczna danych zostanie wyczyszona po zapisaniu i zamknięciu dokumentu.

## <a name="access-typed-datasets-in-the-cache"></a>Uzyskiwanie dostępu do typowanych zestawów danych w pamięci podręcznej
 Jeśli chcesz uzyskać dostęp do danych w typiowym zestawie danych zarówno z rozwiązania pakietu Office, jak i z aplikacji spoza pakietu Office, takiej jak aplikacja usługi Windows Forms lub projekt, musisz zdefiniować typowany zestaw danych w oddzielnym zestawie, do którego odwołuje się oba [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projekty. Jeśli dodasz typowany zestaw danych do  każdego projektu przy użyciu kreatora konfiguracji źródła danych lub narzędzia **Projektant obiektów Dataset,**.NET Framework będzie traktować typowane zestawy danych w tych dwóch projektach jako różne typy. Aby uzyskać więcej informacji na temat tworzenia typów zestawów danych, zobacz Tworzenie i konfigurowanie zestawów danych w [programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)