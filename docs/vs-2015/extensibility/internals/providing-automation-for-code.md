---
title: Zapewnianie automatyzacji kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755626"
---
# <a name="providing-automation-for-code"></a>Zapewnianie automatyzacji kodu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzenie modelu automatyzacji dla kodu nie jest wymagana. Zestaw SDK środowiska nie zapewnia próbkę aby to zrobić. Szczegółowe informacje na temat modele kodu, zobacz <xref:EnvDTE.CodeModel> obiektu.  
  
 Aby zaimplementować modelu kodu, należy zaimplementować żadnych interfejsów, które są określane przez strukturę danych wewnętrznych. Obiekty musi pochodzić od `IDispatch` klasy.  
  
 Obiekty, które można rozszerzyć <xref:EnvDTE.CodeModel> i <xref:EnvDTE.FileCodeModel>, są dostępne z <xref:EnvDTE.Project> obiektu i wyglądać podobnie do następującego:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Możesz wybrać opcję wdrożenia po prostu z `CodeModel` lub `FileCodeModel` interfejsu w obiekcie zwracanie z Twojej `Project` i <xref:EnvDTE.ProjectItem> obiektów. Można korzystać z funkcji w tym interfejsie, który jest odpowiedni dla używanego systemu projektu.  
  
 Jeśli chcesz dodać funkcje, takie jak metody lub właściwości, które nie są dostępne ze standardu `CodeModel` i `FileCodeModel` interfejsów, utworzyć własny interfejs, który dziedziczy standard. Pamiętaj dokumentów za pomocą systemu projektu, aby użytkownicy końcowi będą wiedzieli, do wyszukania go. Zwraca standardowy interfejs, ale użytkownik może wywołać `QueryInterface` metody lub Rzutowanie do interfejsu, jeśli jest on znany istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)
