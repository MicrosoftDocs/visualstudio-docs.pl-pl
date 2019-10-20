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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672989"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dane można wyświetlić użytkownikom aplikacji przez powiązanie danych z Windows Forms. Aby utworzyć te kontrolki powiązane z danymi, możesz przeciągnąć elementy z okna **źródła danych** na Projektant formularzy systemu Windows w programie Visual Studio. W tym temacie opisano niektóre z najpopularniejszych zadań, narzędzi i klas związanych z tworzeniem aplikacji Windows Forms powiązanych z danymi.

 ![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png "raddata operacji przeciągania źródła danych")

 Aby uzyskać ogólne informacje na temat sposobu tworzenia formantów powiązanych z danymi w programie Visual Studio, zobacz [Powiązywanie formantów z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat powiązania danych w Windows Forms, zobacz [Windows Forms powiązania danych](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

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
 Składnik <xref:System.Windows.Forms.BindingSource> służy do dwóch celów. Po pierwsze zapewnia warstwę abstrakcji podczas wiązania kontrolek w formularzu z danymi. Kontrolki w formularzu są powiązane ze składnikiem <xref:System.Windows.Forms.BindingSource> (nie można bezpośrednio powiązać ze źródłem danych).

 Następnie może zarządzać kolekcją obiektów. Dodanie typu do <xref:System.Windows.Forms.BindingSource> powoduje utworzenie listy tego typu.

 Aby uzyskać więcej informacji na temat składnika <xref:System.Windows.Forms.BindingSource>, zobacz:

- [BindingSource, składnik](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [BindingSource, składnik — omówienie](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [BindingSource, składnik — architektura](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator — kontrolka
 Ten składnik udostępnia interfejs użytkownika służący do nawigowania po danych wyświetlanych przez aplikację systemu Windows. Aby uzyskać więcej informacji, zobacz [BindingNavigator Control](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView — formant
 Aby wyświetlić i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych, użyj kontrolki <xref:System.Windows.Forms.DataGridView>. Dane można powiązać z <xref:System.Windows.Forms.DataGridView> przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Aby uzyskać więcej informacji, zobacz [formant DataGridView — Omówienie](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
