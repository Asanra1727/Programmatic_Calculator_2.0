//
//  ViewController.swift
//  ProgrammaticCalculatorApp2.0
//
//  Created by Sanra Mansoor on 09/05/2022.
//

import UIKit

class ViewController: UIViewController {

    @IBOutlet var holder: UIView!
    
    var firstDigit = 0
    var resultDigit = 0
    var currentMathOperators: mathOperators?
    
    enum mathOperators {
        
        case add, subtract, multiply, divide
    }
    
    private var resultLabel: UILabel = {
        let label = UILabel()
        label.text = ""
        label.textColor = .white
        label.textAlignment = .right
        label.font = UIFont(name: "Helvetica", size: 100)
        
        return label
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
    }

    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        
        setUpNumberKeys()
    }
    
    private func setUpNumberKeys() {
        let buttonSize: CGFloat = view.frame.size.width / 4
        
        let buttonZero = UIButton(frame: CGRect(x: 0, y: holder.frame.size.height-buttonSize, width: buttonSize*3, height: buttonSize))
        
        buttonZero.setTitleColor(.white, for: .normal)
        buttonZero.backgroundColor = .darkGray
        buttonZero.setTitle("0", for: .normal)
        buttonZero.tag = 1
        holder.addSubview(buttonZero)
        
        buttonZero.addTarget(self, action: #selector(zeroPressed), for: .touchUpInside)
        
        for x in 0..<3 {
            let buttonOne = UIButton(frame: CGRect(x: buttonSize * CGFloat(x), y: holder.frame.size.height-(buttonSize*2), width: buttonSize, height: buttonSize))
            buttonOne.setTitleColor(.white, for: .normal)
            buttonOne.backgroundColor = .darkGray
            buttonOne.setTitle("\(x+1)", for: .normal)
            buttonOne.tag = x+2
            holder.addSubview(buttonOne)
            buttonOne.addTarget(self, action: #selector(buttonPressed(_:)), for: .touchUpInside)

        }
        
        for x in 0..<3 {
            let buttonTwo = UIButton(frame: CGRect(x: buttonSize * CGFloat(x), y: holder.frame.size.height-(buttonSize*3), width: buttonSize, height: buttonSize))
            buttonTwo.setTitleColor(.white, for: .normal)
            buttonTwo.backgroundColor = .darkGray
            buttonTwo.setTitle("\(x+4)", for: .normal)
            buttonTwo.tag = x+5
            holder.addSubview(buttonTwo)
            buttonTwo.addTarget(self, action: #selector(buttonPressed(_:)), for: .touchUpInside)

    }
        
        for x in 0..<3 {
            let buttonThree = UIButton(frame: CGRect(x: buttonSize * CGFloat(x), y: holder.frame.size.height-(buttonSize*4), width: buttonSize, height: buttonSize))
            buttonThree.setTitleColor(.white, for: .normal)
            buttonThree.backgroundColor = .darkGray
            buttonThree.setTitle("\(x+7)", for: .normal)
            buttonThree.tag = x+8
            holder.addSubview(buttonThree)
            buttonThree.addTarget(self, action: #selector(buttonPressed(_:)), for: .touchUpInside)

}
        let clearAllButton = UIButton(frame: CGRect(x: 0, y: holder.frame.size.height-(buttonSize*5), width: view.frame.size.width - buttonSize, height: buttonSize))
        
        clearAllButton.setTitleColor(.white, for: .normal)
        clearAllButton.backgroundColor = .darkGray
        clearAllButton.setTitle("A/C", for: .normal)
        holder.addSubview(clearAllButton)
        
        
        let mathOperators = ["=", "+", "-", "x", "/"]
        for x in 0..<5 {
            let buttonFour = UIButton(frame: CGRect(x: buttonSize * 3, y: holder.frame.size.height-(buttonSize * CGFloat(x+1)), width: buttonSize, height: buttonSize))
            buttonFour.setTitleColor(.white, for: .normal)
            buttonFour.backgroundColor = .orange
            buttonFour.setTitle(mathOperators[x], for: .normal)
            holder.addSubview(buttonFour)
            buttonFour.tag = x+1
            buttonFour.addTarget(self, action: #selector(mathOperatorsPressed(_:)), for: .touchUpInside)


    }
        
        resultLabel.frame = CGRect(x: 20, y: clearAllButton.frame.origin.y - 110.0, width: view.frame.size.width - 40, height: 100)
        holder.addSubview(resultLabel)
        
        clearAllButton.addTarget(self, action: #selector(clearFunction), for: .touchUpInside)
}
    @objc func clearFunction() {
        
        resultLabel.text = "0"
        currentMathOperators = nil
        firstDigit = 0
    }
    
    @objc func zeroPressed() {
        
        if resultLabel.text != "0" {
        if let text = resultLabel.text {
            resultLabel.text = "\(text)\(0)"
        }
        }
    }
    
    @objc func buttonPressed(_ sender: UIButton) {
        
        let tag = sender.tag - 1
        
        if resultLabel.text == "0" {
            resultLabel.text = "\(tag)"
        }
        else if let text = resultLabel.text {
            resultLabel.text = "\(text)\(tag)"
        }
    }
    
    @objc func mathOperatorsPressed(_ sender: UIButton) {
        
        let tag = sender.tag
        
        if let text = resultLabel.text, let value = Int(text), firstDigit == 0 {
            
            firstDigit = value
            
            resultLabel.text = "0"
        }
        
        
        
        if tag == 1{
            if let mathOperators = currentMathOperators {
                var secondDigit = 0
                if let text = resultLabel.text, let value = Int(text) {
                    secondDigit = value
                }
                
                switch mathOperators {
                case .add:
                    
                    let result = firstDigit + secondDigit
                    resultLabel.text = "\(result)"
                    
                    break
                case .subtract:
                    
                    let result = firstDigit - secondDigit
                    resultLabel.text = "\(result)"
                    break
                case .multiply:
                    
                    let result = firstDigit * secondDigit
                    resultLabel.text = "\(result)"

                    break
                case .divide:
                    
                    let result = firstDigit / secondDigit
                    resultLabel.text = "\(result)"

                    break
                }
            }
            
        }
        else if tag == 2 {
            
            currentMathOperators = .add
        }
        else if tag == 3 {
            
            currentMathOperators = .subtract
            
        }
        else if tag == 4 {
            
            currentMathOperators = .multiply
    }
        else if tag == 5 {
            
            currentMathOperators = .divide
        }

    
}
    
}
