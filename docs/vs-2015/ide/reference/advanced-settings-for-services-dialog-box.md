---
title: Zaawansowane ustawienia dla usług, okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2565b3b8fd84714693661fcf0cf04961a70d10f9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652946"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Zaawansowane ustawienia dla usług — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługi aplikacji klienta zapewniają uproszczony dostęp do [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] logowania, ról i usług profilu z aplikacji Windows Forms i Windows Presentation Foundation (WPF). Możesz użyć **usług** strony w **projektanta projektu** do skonfigurowania usług aplikacji klienta. Aby uzyskać więcej informacji na temat **usług** stronie, zobacz [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md).  
  
 Użyj **ustawienia zaawansowane dla usług** okna dialogowego **usług** strony w **projektanta projektu** Aby skonfigurować ustawienia zaawansowane dla usług aplikacji klienta. Za pomocą tych ustawień, można zastąpić niektóre zachowania domyślne aplikacji usługa mniej typowych scenariuszy. Aby uzyskać więcej informacji, zobacz [usług aplikacji klienta](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Aby uzyskać dostęp do **Zaawansowane ustawienia dla usług** okna dialogowego wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij przycisk **właściwości** na **projektu**  menu. Gdy **projektanta projektu** pojawi się, kliknij przycisk **usług** kartę, a następnie kliknij przycisk **zaawansowane** przycisk. Ten przycisk, zostaną wyłączone do czasu włączenia usługi aplikacji klienta.  
  
## <a name="task-list"></a>Lista zadań  
 [Instrukcje: Konfigurowanie usług aplikacji klienta](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [Instrukcje: Praca w trybie Offline przy użyciu usług aplikacji klienta](http://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Zapisz wartość skrótu hasła lokalnie, aby włączyć logowanie w trybie offline**  
 Określa, czy zaszyfrowane hasło użytkownika będą buforowane lokalnie do użytkownika zalogować się, gdy aplikacja jest w trybie offline. Aby uzyskać więcej informacji, zobacz [jak: Praca w trybie Offline przy użyciu usług aplikacji klienta](http://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Ta opcja jest domyślnie wybrana.  
  
 **Wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie serwera**  
 Określa, czy wcześniej uwierzytelnieni użytkownicy są automatycznie ponownie uwierzytelniany po aplikacja uzyskuje dostęp do ról lub profilu usługi i pliku cookie uwierzytelniania serwera utracił ważność. Wybierz tę opcję, aby odmówić dostępu do usług aplikacji i wymaga jawnego ponownego uwierzytelnienia, po wygaśnięciu pliku cookie. Jest to przydatne w przypadku aplikacji wdrożonych w miejscach publicznych upewnić się, czy użytkownicy, którzy aplikacja działa po użyciu nie pozostanie uwierzytelniony przez czas nieokreślony. Ta opcja jest domyślnie wyczyszczone.  
  
 **Limit czasu pamięci podręcznej usługi roli**  
 Określa ilość czasu, Dostawca roli klienta będzie używać wartości roli pamięci podręcznej, zamiast uzyskiwanie dostępu do usługi ról. Ustaw dany interwał czasu małej wartości, gdy role są aktualizowane często lub większej wartości role są rzadko aktualizowane. Wartość domyślna to jeden dzień.  
  
 Dostawcy ról uzyskuje dostęp do wartości pamięci podręcznej roli lub usługi ról podczas wywoływania <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo wyczyścić pamięć podręczną i wymusić tę metodę w celu uzyskania dostępu do usługi zdalnej, należy wywołać <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody.  
  
 **Użyj niestandardowego ciągu połączenia**  
 Określa, czy dostawcy usług klienta będzie używał niestandardowego magazynu danych dla lokalnej pamięci podręcznej. Domyślnie dostawców usług użyje lokalnego systemu plików w pamięci podręcznej. Wybranie tej opcji automatycznie spowoduje wypełnienie pola tekstowego przy użyciu domyślne parametry połączenia. Możesz zachować domyślne parametry połączenia, aby automatycznie generować i korzystania z bazy danych programu SQL Server Compact Edition, lub można określić parametry połączenia do istniejącej bazy danych programu SQL Server. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie usług aplikacji klienckich](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Ta opcja jest domyślnie wyczyszczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienta](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Strona usług, Projektant projektu](../../ide/reference/services-page-project-designer.md)   
 [Instrukcje: Konfigurowanie usług aplikacji klienta](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Instrukcje: Praca w trybie Offline przy użyciu usług aplikacji klienta](http://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
