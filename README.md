# AlamofireSwiftyJSON


```swift
import Alamofire
import SwiftyJSON

let url = URL(string: "https://translate.googleapis.com/translate_a/single?client=gtx&sl=en&tl=tr&dt=t&q=\(self.wordInputTextFiled.text!)")!
            
            
            AF.request(url)
                        .responseData { response in
                            switch response.result {
                            case .success(let value):
                                let json = JSON(value)
                                DispatchQueue.main.async {
                                    
                                    print(json[0][0][0])
                                }
                                
                            case let .failure(error):
                                print(error.localizedDescription)
                            }
                        }
            
