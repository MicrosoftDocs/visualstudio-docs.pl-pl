---
title: Relacje w zestawach danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e78b4efa9c56a46ea182d3ff3b77a7452d0c547f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755492"
---
# <a name="relationships-in-datasets"></a>Relacje w zestawach danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zestawy danych, które zawierają dane powiązane tabele użyj <xref:System.Data.DataRelation> obiekty do reprezentowania relacji nadrzędny/podrzędny między tabelami i zwrócić powiązanych rekordów od siebie nawzajem. Dodawanie powiązanych tabel do zestawów danych przy użyciu **Kreatora konfiguracji źródła danych**, lub **Projektanta obiektów Dataset**, tworzy i konfiguruje <xref:System.Data.DataRelation> obiekt dla Ciebie.  
  
 <xref:System.Data.DataRelation> Obiektu wykonuje dwie funkcje:  
  
- Może sprawić, że dostępne rekordy związane z rekordu, którą pracujesz. Zawiera rekordy podrzędne, jeśli rekord nadrzędny (<xref:System.Data.DataRow.GetChildRows%2A>) i rekord nadrzędny, jeśli pracujesz z podrzędnego rekordu (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
- Jak również wymuszać ograniczenia integralności referencyjnej, takie jak usuwanie powiązane rekordy podrzędne, po usunięciu rekordu nadrzędnego.  
  
  Należy zrozumieć różnicę między true dołączania i funkcja <xref:System.Data.DataRelation> obiektu. Wartość true, sprzężenia rekordy są pobierane z nadrzędną i podrzędną i umieszczane w jednej, prostego zestawu rekordów. Kiedy używasz <xref:System.Data.DataRelation> obiektu nie nowy zestaw rekordów jest tworzony. Zamiast tego należy DataRelation śledzi relacje między tabelami i elementy nadrzędne i podrzędne rekordy w synchronizacji.  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation — obiekty i ograniczenia  
 Element <xref:System.Data.DataRelation> obiektu umożliwia również tworzenie i wymuszanie następujące ograniczenia:  
  
- Ograniczenia unique, co gwarantuje, że kolumna w tabeli nie zawiera duplikatów.  
  
- Ograniczenie klucza obcego, która może służyć do zachowania więzów integralności między tabelą nadrzędną i podrzędną w zestawie danych.  
  
  Ograniczenia, które są określone w <xref:System.Data.DataRelation> obiektu są implementowane przez automatyczne tworzenie odpowiednich obiektów lub ustawienie właściwości. Jeśli tworzysz ograniczenie klucza obcego przy użyciu <xref:System.Data.DataRelation> object, wystąpień <xref:System.Data.ForeignKeyConstraint> klasy są dodawane do <xref:System.Data.DataRelation> obiektu <xref:System.Data.DataRelation.ChildKeyConstraint%2A> właściwości.  
  
  Zaimplementowano ograniczenia unique albo po prostu ustawiając <xref:System.Data.DataColumn.Unique%2A> właściwości kolumny danych `true` lub dodając wystąpienie <xref:System.Data.UniqueConstraint> klasy <xref:System.Data.DataRelation> obiektu <xref:System.Data.DataRelation.ParentKeyConstraint%2A> właściwości. Aby uzyskać informacji na temat wstrzymywania ograniczenia w zestawie danych, zobacz [wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Zasady integralności referencyjnej  
 W ramach ograniczeń klucza obcego można określić reguły więzów integralności, które są stosowane w trzech miejscach:  
  
- Gdy rekord nadrzędny jest aktualizowany  
  
- Gdy rekord nadrzędny jest usunięty  
  
- Po zmianie jest zaakceptowane lub odrzucone  
  
  Reguły, które można wprowadzić są określone w <xref:System.Data.Rule> wyliczenie i są wymienione w poniższej tabeli.  
  
|Zasada ograniczenia PRIMARY key obcych|Akcja|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|Zmiana (update lub delete), wprowadzone do nadrzędnego rekordu jest również w powiązanych rekordach w tabeli podrzędnej.|  
|<xref:System.Data.Rule>|Rekordy podrzędne nie są usuwane, ale ustawiono klucza obcego w rekordy podrzędne <xref:System.DBNull>. To ustawienie, rekordy podrzędne może pozostać "porzucone" — oznacza to, że ich nie mają relacji z rekordów nadrzędnych. **Uwaga:**  Przy użyciu tej reguły może spowodować nieprawidłowe dane w tabeli podrzędnej.|  
|<xref:System.Data.Rule>|Klucza obcego w powiązanych rekordach podrzędnych jest ustawiona na wartość domyślną (jak ustalono przez wartość z kolumny <xref:System.Data.DataColumn.DefaultValue%2A> właściwości).|  
|<xref:System.Data.Rule>|Nie zmian do powiązane rekordy podrzędne. To ustawienie, rekordy podrzędne mogą zawierać odwołania do rekordów nieprawidłowy element nadrzędny.|  
  
 Aby uzyskać więcej informacji na temat aktualizacji w tabelach zestawu danych, zobacz [zapisać dane w bazie danych](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Tylko ograniczenie relacji  
 Po utworzeniu <xref:System.Data.DataRelation> obiektu, masz możliwość określenia, czy relacja umożliwia tylko wymuszać ograniczenia — oznacza to, go nie również posłuży do uzyskiwania dostępu do rekordów pokrewnych. Ta opcja umożliwia generowanie zestawu danych jest nieco bardziej efektywne i zawiera metody mniej niż jeden możliwości związane z rekordów. Jednak nie można uzyskać dostęp do powiązanych rekordów. Na przykład relacji tylko do ograniczenia uniemożliwia usunięcie rekordu nadrzędnego, który wciąż ma rekordy podrzędne i nie masz dostępu do rekordów podrzędnych przez nadrzędne.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Ręczne tworzenie relacji danych w Projektancie obiektów Dataset  
 Podczas tworzenia tabel danych za pomocą narzędzi do projektowania danych w programie Visual Studio, relacje zostaną utworzone automatycznie, jeśli można gromadzić dane ze źródła danych. Jeśli ręcznie dodasz tabel danych z **DataSet** karcie **przybornika**, może być konieczne ręczne tworzenie relacji. Aby uzyskać informacje na temat tworzenia <xref:System.Data.DataRelation> obiektów programowo, zobacz [Dodawanie elementów DataRelation](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).  
  
 Relacje między tabelami danych są wyświetlane jako wiersze w **Projektanta obiektów Dataset**, za pomocą klucza i nieskończoności glif przedstawiające jeden do wielu aspektów relacji. Domyślnie nazwa relationshipCommentEnd Id = "1c8c78e19b7fa441" nie jest wyświetlany na powierzchni projektowej.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Można utworzyć relacji między tabelami danych dwa  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [jak: Otwórz zestaw danych w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Przeciągnij **relacji** obiektu z **DataSet** przybornika do tabeli podrzędnej danych w relacji.  
  
     **Relacji** zostanie otwarte okno dialogowe wypełnianie **tabeli podrzędnej** pola z tabeli, która została przeciągnięta **relacji** obiektu na.  
  
3.  Wybieranie tabeli nadrzędnej z **tabeli nadrzędnej** pole. Tabela nadrzędna zawiera rekordy na stronie "jeden" w relacji jeden do wielu.  
  
4.  Sprawdź, czy tabela podrzędna poprawne są wyświetlane w **tabeli podrzędnej** pole. Tabela podrzędna zawiera rekordy na stronie "many" w relacji jeden do wielu.  
  
5.  Wpisz nazwę dla relacji w **nazwa** pole lub pozostaw nazwę domyślną, w oparciu o wybrane tabele. Jest to nazwa rzeczywistych <xref:System.Data.DataRelation> obiektu w kodzie.  
  
6.  Wybierz kolumny, które sprzężenia w **kolumn klucza** i **kolumny klucza obcego** listy.  
  
7.  Wybierz, czy chcesz utworzyć relację i/lub ograniczenia. Aby uzyskać informacje, zobacz [wprowadzenie do obiektów DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
8.  Zaznacz lub wyczyść **zagnieżdżone relacji** pole. Wybranie tej opcji ustawia <xref:System.Data.DataRelation.Nested%2A> właściwości `true`, i sprawia, że element podrzędny wiersze w relacji do być zagnieżdżony w kolumnie nadrzędnej, gdy te wiersze są zapisywane w postaci danych XML lub synchronizowane z <xref:System.Xml.XmlDataDocument>. Aby uzyskać więcej informacji, zobacz [zagnieżdżanie elementów DataRelation](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).  
  
9. Ustawianie reguł, które mają być egzekwowane, gdy wprowadzasz zmiany do rekordów w tych tabelach. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Rule>.  
  
10. Kliknij przycisk **OK** do utworzenia relacji. Zostanie wyświetlony wiersz relacji w Projektancie między dwiema tabelami.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Aby wyświetlić nazwy relacji w Projektancie obiektów Dataset  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [jak: Otwórz zestaw danych w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Z **danych** menu, wybierz opcję **Pokaż etykiety relacji** polecenie, aby wyświetlić nazwę relacji. Usuń zaznaczenie tego polecenia, aby ukryć nazwę relacji.
