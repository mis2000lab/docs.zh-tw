---
title: 如何： 共用組件與其他應用程式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 3a6a04a3aef5430eb65d0c1a7eb37f6afb9e5c86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>如何： 共用組件與其他應用程式 (Visual Basic)
組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。  
  
 為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。  
  
### <a name="sharing-an-assembly"></a>共用組件  
  
1.  建立您的組件。 如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。  
  
2.  為您的組件指派強式名稱。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
3.  將版本資訊指派給您的組件。 如需詳細資訊，請參閱[組件版本控制](../../../../framework/app-domains/assembly-versioning.md)。  
  
4.  將您的組件新增至全域組件快取。 如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。  
  
5.  從其他應用程式存取組件內含的類型。 如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)[組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [使用組件設計程式](../../../../framework/app-domains/programming-with-assemblies.md)
