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
            



                                name: json["name"].rawValue as! String,
                                temp: Int(json["main"]["temp"].rawValue as! Double), temp_min: Int(json["main"]["temp_min"].rawValue as! Double),
                                temp_max: Int(json["main"]["temp_max"].rawValue as! Double),
                                weather: "\(json["weather"].array![0]["main"])",
