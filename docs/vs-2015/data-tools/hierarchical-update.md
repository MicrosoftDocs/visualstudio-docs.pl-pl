---
title: Hierarchiczna aktualizacja | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 17eb5c1ca2ad35b7a510c5a70d3ad5c5f741c69d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063403"
---
# <a name="hierarchical-update"></a>Hierarchiczna aktualizacja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hierarchiczna aktualizacja * odnosi się do procesu zapisywanie zaktualizowanych danych (na podstawie zestawu danych przy użyciu dwóch lub więcej powiązanych tabel) do bazy danych przy zachowaniu więzy integralności. *Integralność referencyjną* odwołuje się do reguły spójności, dostarczone przez ograniczenia w bazie danych, które kontrolują zachowanie Wstawianie, aktualizowanie i usuwanie rekordów pokrewnych. Na przykład jest więzów integralności, który wymusza utworzenie rekordu klientów przed zezwoleniem zamówienia, które ma zostać utworzony dla tego klienta.  Aby uzyskać więcej informacji na temat relacji w zestawach danych, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md)  
  
 Używa funkcji hierarchiczna aktualizacja `TableAdapterManager` zarządzanie `TableAdapter`s w zestawie danych wpisywanych. `TableAdapterManager` Składnik to [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-wygenerowane klasy, dlatego nie jest częścią [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Podczas przeciągania tabeli z okna źródeł danych do postaci Windows lub strony WPF program Visual Studio dodaje zmienną typu TableAdapterManager do formularza lub strony, a zostanie wyświetlony w projektancie w zasobniku składnika. Aby uzyskać szczegółowe informacje na temat `TableAdapterManager` klasy, zobacz sekcję TableAdapterManager z [TableAdapterManager — Przegląd](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Domyślnie zestaw traktuje powiązane tabele jako "tylko relacje" oznacza to, że nie to wymuszania ograniczeń klucza obcego. Możesz zmodyfikować to ustawienie w czasie projektowania za pomocą Projektanta obiektów Dataset. Zaznacz wiersz relacji między dwiema tabelami, aby wyświetlić **relacji** okno dialogowe. Zmiany wprowadzone w tym miejscu będzie określają sposób TableAdapterManager zachowania, gdy jest w stanie wysyłać zmian w tabelach pokrewnych w bazie danych.  
  
## <a name="enablehierarchical-update-in-a-dataset"></a>Aktualizacja Enablehierarchical w zestawie danych  
 Domyślnie hierarchiczna aktualizacja jest włączona dla wszystkich nowych zestawów danych, które są dodawane lub utworzone w projekcie. Włączyć lub wyłączyć aktualizację hierarchiczną, ustawiając **hierarchicznej aktualizacji** właściwość typizowany zestaw danych w Projektancie obiektów DataSet, aby **True** lub **False**:  
  
 ![Ustawienia aktualizacji hierarchicznej](../data-tools/media/hierarchical-update-setting.png "ustawienie hierarchicznej aktualizacji")  
  
## <a name="create-a-new-relation-between-tables"></a>Tworzenie nowej relacji między tabelami  
 Aby utworzyć nową relację między dwiema tabelami, w Projektancie obiektów Dataset, wybierz pasek tytułu w każdej tabeli, a następnie kliknij prawym przyciskiem myszy i wybierz**Dodaj relacje**.  
  
 ![Hierarchiczna aktualizacja dodać menu relacji](../data-tools/media/hierarchical-update-add-relation-menu.png "relacji menu dodawania hierarchicznej aktualizacji")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Omówienie ograniczeń klucza obcego, aktualizacje i usuwanie kaskadowe  
 Jest ważne zrozumieć, jak ograniczenia klucza obcego i kaskadowych zachowanie w bazie danych są tworzone w kodzie wygenerowanego zestawu danych.  
  
 Domyślnie tabele danych w zestawie danych są generowane przy użyciu relacji (<xref:System.Data.DataRelation>) zgodnych relacji w bazie danych. Przyjrzyjmy się relacji w zestawie danych nie jest generowany jako ograniczenie klucza obcego. <xref:System.Data.DataRelation> Jest skonfigurowany jako **tylko relacji** bez <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> lub <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> obowiązywać.  
  
 Domyślnie aktualizacje i usuwanie kaskadowe kaskadowe są wyłączone nawet, jeśli relacje bazy danych została ustawiona za pomocą kaskadowych aktualizacji i/lub usuwanie kaskadowe włączona. Na przykład utworzenie nowego klienta i nowe zamówienia, a następnie próba zapisania danych może powodować konflikt z ograniczenia klucza obcego, które są zdefiniowane w bazie danych. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie ograniczeń klucza obcego w zestawie danych](http://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).  
  
## <a name="set-the-order-to-perform-updates"></a>Ustaw kolejność przeprowadzania aktualizacji  
 Ustawienie kolejności do przeprowadzania aktualizacji ustawia kolejność poszczególnych wstawia, aktualizacji i usunięć, które są wymagane do zapisania zmodyfikowanych danych we wszystkich tabelach zestawu danych. Po włączeniu aktualizacji hierarchicznej wstawia są wykonane jako pierwsze, a następnie aktualizuje, a następnie usuwa. `TableAdapterManager` Zapewnia `UpdateOrder` właściwości, które mogą być zestawem do przeprowadzania aktualizacji po pierwsze, a następnie wstawiania i usuwania.  
  
> [!NOTE]
>  Jest ważne dowiedzieć się, że kolejność aktualizacji jest z uwzględnieniem wszystkich. Oznacza to kiedy aktualizacje są wykonywane, wstawiania i usuwania są wykonywane dla wszystkich tabel w zestawie danych.  
  
 Aby ustawić `UpdateOrder` właściwości po przeciąganie elementów z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) w formularzu Wybierz `TableAdapterManager` w zasobniku składnika, a następnie ustaw `UpdateOrder` właściwości w **właściwości** okna. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie kolejności podczas przeprowadzania hierarchicznej aktualizacji](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).  
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Tworzenie kopii zapasowej zestawu danych przed przystąpieniem do wykonywania hierarchicznej aktualizacji  
 Podczas zapisywania danych (przez wywołanie metody `TableAdapterManager.UpdateAll()` metoda), `TableAdapterManager` próbuje zaktualizować dane dla każdej tabeli w ramach jednej transakcji. Jeśli którejkolwiek aktualizacji dla każdej tabeli zakończy się niepowodzeniem, cała transakcja zostanie wycofana. W większości sytuacji wycofywanie zwraca aplikacji do stanu pierwotnego.  
  
 Jednak czasami warto przywrócić zestawu danych z kopii zapasowej. Przykładem takiej mogą wystąpić podczas korzystania z automatycznego przyrostu wartości. Na przykład, jeśli zapisywania operacja zakończy się niepowodzeniem, automatycznego przyrostu wartości nie są resetowane w zestawie danych i zestaw danych w dalszym ciągu Utwórz auto, zwiększenie wartości. Spowoduje to, że przerwa w numerowania identyfikatorów, które mogą nie być niedopuszczalne w aplikacji. W sytuacjach, w przypadku, gdy jest to problem `TableAdapterManager` zapewnia `BackupDataSetBeforeUpdate` właściwość, która zastępuje istniejący zestaw danych z kopii zapasowej, jeśli transakcja nie powiedzie się.  
  
> [!NOTE]
>  Kopia zapasowa jest tylko w pamięci podczas `TableAdapterManager.UpdateAll` metoda jest uruchomiona. Dlatego ma nie programowy dostęp do tego zestawu kopii zapasowych danych, ponieważ jego albo zastępuje oryginalnego zestawu danych lub wykracza poza zakres jak najszybciej `TableAdapterManager.UpdateAll` metoda odliczania.  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modyfikowanie wygenerowany Zapisz kod do wykonywania hierarchicznej aktualizacji  
 Zapisz zmiany z tabel powiązanych danych w zestawie danych w bazie danych przez wywołanie metody `TableAdapterManager.UpdateAll` metody i przekazywać nazwę zestawu danych, który zawiera powiązane tabele. Na przykład uruchomić `TableAdapterManager.UpdateAll(NorthwindDataset)` metodę, aby wysyłać aktualizacje ze wszystkich tabel w NorthwindDataset do wewnętrznej bazy danych.  
  
 Po upuszczeniu elementy z **źródeł danych** oknie kodu jest automatycznie dodawany do `Form_Load` zdarzenie, aby wypełnić każdej tabeli ( `TableAdapter.Fill` metody). Kod jest także dodawane do **Zapisz** Zdarzenie kliknięcia przycisku <xref:System.Windows.Forms.BindingNavigator> można zapisać danych z zestawu danych w bazie danych ( `TableAdapterManager.UpdateAll` metody).  
  
 Zapisz wygenerowany kod zawiera również linię kodu, który wywołuje `CustomersBindingSource.EndEdit` metody. W szczególności wywołuje <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Metoda pierwszego <xref:System.Windows.Forms.BindingSource>który został dodany do formularza. Innymi słowy, ten kod jest generowany tylko jako pierwszą tabelę, która zostanie przeciągnięty z **źródeł danych** okna na formularzu. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Wywołanie zatwierdza wszystkie zmiany, które jest obecnie w toku w żadnych formantów powiązanych z danymi, które są aktualnie edytowanym. W związku z tym, jeśli formant powiązany z danymi nadal ma fokus i kliknij przycisk **Zapisz** przycisk wszystkie oczekujące zmiany, w tym, że kontrolki są zatwierdzane przed rzeczywiste Zapisz ( `TableAdapterManager.UpdateAll` metody).  
  
> [!NOTE]
>  Dodawanie tylko w Projektancie obiektów Dataset `BindingSource.EndEdit` kod dla pierwszej tabeli, który został upuszczony na formularz. W związku z tym, należy dodać wiersz kodu w celu wywołania `BindingSource.EndEdit` metody dla każdej tabeli powiązanej na formularzu. W tym przewodniku, oznacza to, należy dodać wywołanie `OrdersBindingSource.EndEdit` metody.  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Aby zaktualizować kod w celu zatwierdzenia zmian w tabelach pokrewnych przed zapisaniem  
  
1. Kliknij dwukrotnie **Zapisz** znajdujący się na <xref:System.Windows.Forms.BindingNavigator> otworzyć **Form1** w edytorze kodu.  
  
2. Dodaj wiersz kodu w celu wywołania `OrdersBindingSource.EndEdit` metoda po wierszu, który wywołuje `CustomersBindingSource.EndEdit` metody. Kod w **Zapisz** kliknięcia przycisku zdarzeń powinny wyglądać podobnie do poniższego:  
  
    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]  
  
   Oprócz zatwierdzania zmian w pokrewnej tabeli podrzędnej przed zapisaniem danych do bazy danych, również może być konieczne rekordów nadrzędnych zatwierdzenia nowo utworzony przed dodaniem nowych rekordów podrzędnych do zestawu danych. Innymi słowy trzeba będzie dodać nowy rekord nadrzędny (klienta) do zestawu danych przed ograniczenia klucza obcego włączyć nowe rekordy podrzędne (zamówienia), który ma zostać dodany do zestawu danych. Aby to osiągnąć, należy użyć elementu podrzędnego `BindingSource.AddingNew` zdarzeń.  
  
> [!NOTE]
>  Czy masz do zatwierdzenia nowych rekordów nadrzędnych, zależy od typu formantu, który służy do tworzenia powiązania ze źródłem danych. W tym przewodniku umożliwia pojedynczych formantów powiązania tabeli nadrzędnej. Wymaga to dodatkowego kodu, aby zatwierdzić nowy rekord nadrzędny. Jeśli rekordów nadrzędnych zamiast były wyświetlane w kontrolce złożone powiązanie <xref:System.Windows.Forms.DataGridView>, tym dodatkowe <xref:System.Windows.Forms.BindingSource.EndEdit%2A> wywołania dla rekordu nadrzędnego nie jest konieczne. Jest to spowodowane obsługuje podstawową funkcjonalność powiązanie danych kontrolki, zatwierdzanie nowych rekordów.  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Aby dodać kod, aby zatwierdzić rekordów nadrzędnych w zestawie danych przed dodaniem nowych rekordów podrzędnych  
  
1. Utwórz procedurę obsługi zdarzeń dla `OrdersBindingSource.AddingNew` zdarzeń.  
  
    - Otwórz **Form1** w widoku Projekt, wybierz **OrdersBindingSource** w zasobniku składnika wybierz **zdarzenia** w **właściwości** oknie i następnie kliknij dwukrotnie ikonę **AddingNew** zdarzeń.  
  
2. Dodaj wiersz kodu do obsługi zdarzeń, który wywołuje `CustomersBindingSource.EndEdit` metody. Kod w `OrdersBindingSource_AddingNew` programu obsługi zdarzeń powinny wyglądać podobnie do poniższego:  
  
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]  
  
## <a name="tableadaptermanager-reference"></a>TableAdapterManager odwołania  
 Domyślnie `TableAdapterManager` klasy jest generowany, gdy utworzysz zestaw danych, który zawiera powiązane tabele. Aby zapobiec sytuacji, w której klasy generowane, należy zmienić wartość `Hierarchical Update` właściwości zestawu danych na wartość false. Podczas przeciągania tabeli, która ma relację na powierzchnię projektową formularza Windows lub strony WPF program Visual Studio deklaruje zmienną składową klasy. Nie używaj wiązania danych, musisz ręcznie zadeklarować zmienną.  
  
 `TableAdapterManager` Klasa nie jest częścią [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. W związku z tym użytkownik nie może go wyszukać w dokumentacji. Jest on tworzony w czasie projektowania, jako część procesu tworzenia zestawu danych.  
  
 Poniżej przedstawiono często używanych metod i właściwości `TableAdapterManager` klasy:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`UpdateAll` — Metoda|Zapisuje wszystkie dane ze wszystkich tabel danych.|  
|`BackUpDataSetBeforeUpdate` Właściwość|Określa, czy chcesz utworzyć kopię zapasową danych przed wykonaniem `TableAdapterManager.UpdateAll` metody. Wartość logiczna.|  
|*Właściwość tableName* `TableAdapter` właściwości|Reprezentuje `TableAdapter`. Wygenerowany `TableAdapterManager` zawiera właściwości dla każdego `TableAdapter` zarządza. Na przykład zestaw danych z tabeli Customers i Orders jest generowany przy użyciu `TableAdapterManager` zawierający `CustomersTableAdapter` i `OrdersTableAdapter` właściwości.|  
|`UpdateOrder` Właściwość|Określa kolejność poszczególnych insert, update i polecenia delete. Ustaw tę wartość na jedną z wartości w `TableAdapterManager.UpdateOrderOption` wyliczenia.<br /><br /> Domyślnie `UpdateOrder` ustawiono **InsertUpdateDelete**. Oznacza to, że wstawia, a następnie aktualizuje i usuwa są wykonywane dla wszystkich tabel w zestawie danych. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie kolejności podczas przeprowadzania hierarchicznej aktualizacji](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
