---
title: Powiązywanie kontrolek Windows Forms z danymi
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f2bd51570c8ad1976b6fc9eb5674177f9342833
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069461"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyświetlić dane użytkownikom aplikacji przez powiązanie danych do formularzy Windows Forms. Aby utworzyć te formanty powiązane z danymi, można przeciągnąć elementy z **źródeł danych** okna na Windows Forms Designer w programie Visual Studio. W tym temacie opisano niektóre z najbardziej typowych zadań, narzędzi i klasy związane z tworzeniem aplikacji Windows Forms powiązanych z danymi.

 ![Źródło danych operacji przeciągania](../data-tools/media/raddata-data-source-drag-operation.png "operacji przeciągania raddata źródła danych")

 Aby uzyskać ogólne informacje na temat tworzenia formantów powiązanych z danymi w programie Visual Studio, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat wiązania danych w formularzach Windows Forms, zobacz [powiązanie danych formularzy Windows](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>W tej sekcji

- [Powiązywanie kontrolek Windows Forms z danymi](../data-tools/bind-windows-forms-controls-to-data.md)

- [Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Tworzenie tabel wyszukiwania w aplikacjach Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych](../data-tools/create-a-windows-form-to-search-data.md)

- [Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującego powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Przekazywanie danych między formularzami](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource — składnik
 <xref:System.Windows.Forms.BindingSource> Składnika służy do dwóch celów. Po pierwsze zapewnia warstwę abstrakcji podczas powiązywanie kontrolek w formularzu z danymi. Formanty formularza jest powiązana z <xref:System.Windows.Forms.BindingSource> składnika (zamiast związania bezpośrednio ze źródłem danych).

 Po drugie może zarządzać kolekcji obiektów. Dodawanie typu <xref:System.Windows.Forms.BindingSource> tworzy listę tego typu.

 Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.BindingSource> składników, zobacz:

- [BindingSource, składnik](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [BindingSource, składnik — omówienie](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [BindingSource, składnik — architektura](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator — kontrolka
 Ten składnik udostępnia interfejs użytkownika do przechodzenia między danymi wyświetlanymi przez aplikację Windows. Aby uzyskać więcej informacji, zobacz [BindingNavigator — kontrolka](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView — formant
 Aby wyświetlić i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych, należy użyć <xref:System.Windows.Forms.DataGridView> kontroli. Można powiązać danych <xref:System.Windows.Forms.DataGridView> przy użyciu <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości. Aby uzyskać więcej informacji, zobacz [— informacje o formancie DataGridView](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
