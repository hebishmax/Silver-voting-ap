import { useState } from 'react';
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { ethers } from 'ethers';
import { connectWallet } from '../utils/ethereum';

export default function VotingApp() {
  const [question, setQuestion] = useState("");
  const [voteOptions, setVoteOptions] = useState(["", ""]);
  const [submitting, setSubmitting] = useState(false);

  const handleOptionChange = (index, value) => {
    const newOptions = [...voteOptions];
    newOptions[index] = value;
    setVoteOptions(newOptions);
  };

  const addOption = () => setVoteOptions([...voteOptions, ""]);

  const submitPoll = async () => {
    setSubmitting(true);

    try {
      const signer = await connectWallet();

      const contractAddress = "0xYourSmartContractAddress"; // عدل هنا
      const abi = [/* ضع ABI هنا */];

      const contract = new ethers.Contract(contractAddress, abi, signer);
      const tx = await contract.createPoll(question, voteOptions);
      await tx.wait();

      alert("تم إنشاء الاستطلاع بنجاح!");
    } catch (error) {
      console.error(error);
      alert("حدث خطأ أثناء إنشاء الاستطلاع.");
    }

    setSubmitting(false);
  };

  return (
    <Card className="max-w-xl mx-auto mt-10 p-4">
      <CardContent>
        <Input
          placeholder="اكتب سؤال الاستطلاع"
          value={question}
          onChange={(e) => setQuestion(e.target.value)}
        />
        {voteOptions.map((option, index) => (
          <Input
            key={index}
            placeholder={`خيار ${index + 1}`}
            value={option}
            onChange={(e) => handleOptionChange(index, e.target.value)}
            className="mt-2"
          />
        ))}
        <Button onClick={addOption} className="mt-2">أضف خيار</Button>
        <Button onClick={submitPoll} className="mt-4" disabled={submitting}>
          {submitting ? "...جارٍ الإرسال" : "أنشئ الاستطلاع"}
        </Button>
      </CardContent>
    </Card>
  );
}
