# TapMe-

 主要是timer 和 UIAlertController的使用
 
 import UIKit

class ViewController: UIViewController {
    
    
    @IBOutlet weak var timerLabel: UILabel!
    
    @IBOutlet weak var scoreLabel: UILabel!
    
    var count = 0
    
    @IBAction func buttonPressed(){
        NSLog("Button Pressed")
        scoreLabel.text = "score is \n\(count)"
        count++
    }
    
    var second = 0
    var timer = NSTimer()
    
    func setupGame(){
        second = 30
        count = 0
        
        timerLabel.text = "Timer : \(second)"
        scoreLabel.text = "Score : \(count)"
        
        timer = NSTimer.scheduledTimerWithTimeInterval(0.1, target: self , selector: Selector("subtracTime"), userInfo: nil, repeats: true)
    }
    
    func subtracTime(){
        second--
        timerLabel.text = "Timer : \(second)"

        if (second == 0){
           timer.invalidate()
            
           let alert = UIAlertController(title: "Time is up!", message: "You score\(count) Points", preferredStyle: UIAlertControllerStyle.Alert)
            alert.addAction(UIAlertAction(title:"Play again" , style: UIAlertActionStyle.Default, handler: {action in self.setupGame()}))
            presentViewController(alert, animated: true, completion:nil)
        }
        
    }
    

    override func viewDidLoad() {
        super.viewDidLoad()
        
        setupGame()
        
        
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        
    }


}

